### <a name="winforms-checkforoverflowunderflow-property-is-now-true-for-systemdrawing"></a>WinForm'ın CheckForOverflowUnderflow özelliği System.Drawing için geçerlidir

|   |   |
|---|---|
|Ayrıntılar|System.Drawing.dll derleme için CheckForOverflowUnderflow özelliğinin true.|
|Öneri|Daha önce taşmalar oluştuğunda, sonuç sessizce kesilebilir. Şimdi bir <xref:System.OverflowException?displayProperty=name> özel durumu oluşur.|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|çalışma zamanı|

