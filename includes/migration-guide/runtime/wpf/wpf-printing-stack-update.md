### <a name="wpf-printing-stack-update"></a>WPF yazdırma yığını güncelleştirmesi

|   |   |
|---|---|
|Ayrıntılar|WPF'nin yazdırma API'lerini kullanarak <xref:System.Printing.PrintQueue?displayProperty=name> penceresinin Yazdır belge paket API artık kullanım dışı XPS yazdırma API yerine artık çağırın. Bakım kolaylığı düşünülerek ile değişiklik yapılmıştır; kullanıcıların ne geliştiricilerin herhangi bir değişiklik davranış veya API kullanımı görmeniz gerekir. Yeni yazdırma yığın içinde Windows 10 Creators Update çalıştıran, varsayılan olarak etkindir. Eski yazdırma yığın hala eski Windows sürümlerinde yalnızca önceki gibi çalışmaya devam eder.|
|Öneri|Eski yığın içinde Windows 10 Creators Update kullanmak için ayarlanmış <code>UseXpsOMPrinting</code> REG_DWORD değeri <code>HKEY_CURRENT_USER\Software\Microsoft\.NETFramework\Windows Presentation Foundation\Printing</code> kayıt defteri anahtarına <code>1</code>.|
|Kapsam|Kenar|
|Sürüm|4.7|
|Tür|Çalışma zamanı|

