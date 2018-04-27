### <a name="wpf-printing-stack-update"></a>WPF yazdırma yığın güncelleştirme

|   |   |
|---|---|
|Ayrıntılar|WPF'ın yazdırma API'lerini kullanarak <xref:System.Printing.PrintQueue?displayProperty=name> Şimdi pencerenin yazdırma belge paket API artık kullanım dışı XPS yazdırma API lehinde çağırın. Bakım kolaylığı aklınızda ile değişikliğin yapıldığı; kullanıcıların ne geliştiriciler davranışı veya API kullanımı değişiklikler görmeniz gerekir. Yeni yazdırma yığını, Windows 10 oluşturucuları güncelleştirmede çalıştırırken varsayılan olarak etkindir. Eski yazdırma yığını hala eski Windows sürümlerinde yalnızca eskisi çalışmaya devam eder.|
|Öneri|Windows 10 oluşturucuları güncelleştirmede eski yığını kullanmak üzere ayarlanmış <code>UseXpsOMPrinting</code> REG_DWORD değerini <code>HKEY_CURRENT_USER\Software\Microsoft\.NETFramework\Windows Presentation Foundation\Printing</code> kayıt defteri anahtarına <code>1</code>.|
|Kapsam|Kenar|
|Sürüm|4.7|
|Tür|Çalışma zamanı|

