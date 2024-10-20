import numpy as np
from matplotlib import pyplot as plt
from scipy.optimize import curve_fit

# Função de ajuste (hipotética, precisa ser confirmada)
def fit_f(i, B, L):
    return i * L * B

# Aquisição dos dados
i = np.array([0,0.5,1,1.5,2,2.5,3,3.5,4,4.5])
L_1 = 0.0125
L_2 = 0.025
L_3 = 0.05
L_4 = 0.1
f_l1 = np.array([31.5, 31.55, 31.63, 31.7, 31.74, 31.82, 31.9, 31.94, 32, 32.04])
f_l2 = np.array([30.65, 30.8, 30.92, 31.03, 31.15, 31.25, 31.36, 31.5, 31.63, 31.73])
f_l3 = np.array([37.86, 38.1, 38.31, 38.53, 38.72, 38.94, 39.15, 39.4, 39.62, 39.71])
f_l4 = np.array([40.31, 40.75, 41.15, 41.5, 41.97, 42.42, 42.83, 43.22, 43.64, 44.04])

# Plotando os gráficos
plt.scatter(i, f_l1, c='r', label="L_1")
plt.scatter(i, f_l2, c='g', label="L_2")
plt.scatter(i, f_l3, c='b', label="L_3")
plt.scatter(i, f_l4, c='k', label="L_4")
plt.legend(loc="upper left")
plt.xlabel("Corrente")
plt.ylabel("Força magnética")
plt.show()

# Tratamento dos dados
f_l1_novo = (f_l1 - f_l1[0]) * 9.8
f_l2_novo = (f_l2 - f_l2[0]) * 9.8
f_l3_novo = (f_l3 - f_l3[0]) * 9.8
f_l4_novo = (f_l4 - f_l4[0]) * 9.8

# Plotando os gráficos tratados
plt.scatter(i, f_l1_novo, c='r', label="L_1")
plt.scatter(i, f_l2_novo, c='g', label="L_2")
plt.scatter(i, f_l3_novo, c='b', label="L_3")
plt.scatter(i, f_l4_novo, c='k', label="L_4")
plt.legend(loc="upper left")
plt.xlabel("Corrente")
plt.ylabel("Força magnética (tratada)")
plt.show()

# Aplicação de curve fitting com matriz de covariância
B_1, cov_matrix_1 = curve_fit(lambda i, B: fit_f(i, B, L_1), i, f_l1_novo)
B_2, cov_matrix_2 = curve_fit(lambda i, B: fit_f(i, B, L_2), i, f_l2_novo)
B_3, cov_matrix_3 = curve_fit(lambda i, B: fit_f(i, B, L_3), i, f_l3_novo)
B_4, cov_matrix_4 = curve_fit(lambda i, B: fit_f(i, B, L_4), i, f_l4_novo)

# Exibindo valores ajustados e as matrizes de covariância
print(f"B_1 ajustado: {B_1[0]}, Matriz de Covariância: \n{cov_matrix_1}")
print(f"B_2 ajustado: {B_2[0]}, Matriz de Covariância: \n{cov_matrix_2}")
print(f"B_3 ajustado: {B_3[0]}, Matriz de Covariância: \n{cov_matrix_3}")
print(f"B_4 ajustado: {B_4[0]}, Matriz de Covariância: \n{cov_matrix_4}")

# Plotando o gráfico de teste para L_1 (como exemplo)
plt.scatter(i, f_l1_novo, c='r', label="L_1 obs")
plt.plot(i, fit_f(i, B_1[0], L_1), c='r', label="L_1 pred")

plt.scatter(i, f_l2_novo, c='g', label="L_2 obs")
plt.plot(i, fit_f(i, B_2[0], L_2), c='g', label="L_2 pred")

plt.scatter(i, f_l3_novo, c='b', label="L_3 obs")
plt.plot(i, fit_f(i, B_3[0], L_3), c='b', label="L_3 pred")

plt.scatter(i, f_l4_novo, c='k', label="L_4 obs")
plt.plot(i, fit_f(i, B_4[0], L_4), c='k', label="L_4 pred")

plt.legend(loc="upper left")
plt.xlabel("Corrente")
plt.ylabel("Força magnética (tratada)")
plt.show()
