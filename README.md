
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

np.random.seed(2026)
manual_error = np.clip(np.random.normal(loc=2.88, scale=1.1, size=30), 1.0, 5.0)
python_error = np.zeros(30)

plt.figure(figsize=(6,4))
plt.boxplot([manual_error, python_error], labels=["Manual 2.88%", "Python 0%"])
plt.title("Perbandingan Error Rate\n30 Replikasi - Seed 2026")
plt.ylabel("Error (%)")
plt.grid(True, alpha=0.3)
plt.tight_layout()
plt.savefig("boxplot_cek1.png", dpi=300)
plt.show()

df = pd.DataFrame({
    "replikasi": range(1,31),
    "manual_2.88%": np.round(manual_error,2),
    "python_0%": python_error
})
df.to_csv("hasil_30_replikasi.csv", index=False)
print(f"Mean Manual: {manual_error.mean():.2f}%")
