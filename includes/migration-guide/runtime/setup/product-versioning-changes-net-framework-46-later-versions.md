---
ms.openlocfilehash: 6a79f04af44f78313c4d5bb5c37dfad252d3024b
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496686"
---
### <a name="product-versioning-changes-in-the-net-framework-46-and-later-versions"></a>.NET Framework 4,6 ve sonraki sürümlerde ürün sürümü oluşturma değişiklikleri

#### <a name="details"></a>Ayrıntılar

Ürün sürümü oluşturma, .NET Framework önceki sürümlerinden ve özellikle de .NET Framework 4, 4,5, 4.5.1 ve 4.5.2 ' den değiştirilmiştir. Ayrıntılı değişiklikler aşağıda verilmiştir:<ul><li>Anahtardaki girdinin değeri, <code>Version</code> <code>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full</code> <code>4.6.xxxxx</code> .NET Framework 4,6 ve noktası sürümleri için ve <code>4.7.xxxxx</code> .NET Framework 4,7 ve 4.7.1 için olarak değiştirilmiştir. .NET Framework 4,5, 4.5.1 ve 4.5.2 ' de, biçimi vardı <code>4.5.xxxxx</code> .</li><li>.NET Framework dosyaları için dosya ve ürün sürümü oluşturma daha önceki sürüm 4.0.30319. x ile 4.6. X. 0 ile .NET Framework 4,6 ve onun noktası sürümleri için ve .NET Framework 4,7 ve 4.7.1 için 4.7. X. 0 olarak değiştirilmiştir. Bir dosyaya sağ tıkladıktan sonra dosyanın özelliklerini görüntülerken bu yeni değerleri görebilirsiniz.</li><li><xref:System.Reflection.AssemblyFileVersionAttribute> <xref:System.Reflection.AssemblyInformationalVersionAttribute> Yönetilen derlemelerin ve özniteliklerinin sürüm değerleri, .NET Framework 4,6 ve noktası sürümleri için 4.6. x. 0 biçiminde ve .NET Framework 4,7 ve 4.7.1 için 4.7. x. 0 biçimindedir.</li><li>.NET Framework 4,6, 4.6.1, 4.6.2, 4,7 ve 4.7.1, <xref:System.Environment.Version?displayProperty=nameWithType> özelliği sabit sürüm dizesini döndürür <code>4.0.30319.42000</code> . .NET Framework 4, 4,5, 4.5.1 ve 4.5.2 ' de, sürüm dizelerini biçiminde döndürür <code>4.0.30319.xxxxx</code> (örneğin, &quot; 4.0.30319.18010 &quot; ). Uygulama kodu ' nu Environment. Version özelliği üzerinde herhangi bir yeni bağımlılık alan önermediğimizi unutmayın.</li></ul>Daha fazla bilgi için bkz. [nasıl yapılır: hangi .NET Framework sürümlerinin yüklendiğini belirleme](~/docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md).

#### <a name="suggestion"></a>Öneri

Genel olarak, uygulamalar .NET Framework çalışma zamanı sürümü ve yükleme dizini gibi şeyleri tespit etmek için önerilen tekniklerin üzerine bağımlıdır:<ul><li>.NET Framework çalışma zamanı sürümünü algılamak için bkz. [nasıl yapılır: hangi .NET Framework sürümlerinin yüklendiğini belirleme](~/docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md).</li><li>.NET Framework için yükleme yolunu öğrenmek için, <code>InstallPath</code> anahtardaki girdinin değerini kullanın <code>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full</code> .</li></ul> <blockquote> [!IMPORTANT] Alt anahtar adı <code>NET Framework Setup</code> değil, <code>.NET Framework Setup</code> .</blockquote> <ul><li>.NET Framework ortak dil çalışma zamanının dizin yolunu öğrenmek için <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory?displayProperty=nameWithType> yöntemini çağırın.</li><li>CLR sürümünü almak için <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion?displayProperty=nameWithType> yöntemini çağırın. .NET Framework 4 ve nokta sürümleri (.NET Framework 4,5, 4.5.1, 4.5.2 ve .NET Framework 4,6, 4.6.1, 4.6.2, 4,7 ve 4.7.1) için, v 4.0.30319 dizesini döndürür.</li></ul>

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |İkincil|
|Sürüm|4.6|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

API analizi aracılığıyla algılanamaz.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
