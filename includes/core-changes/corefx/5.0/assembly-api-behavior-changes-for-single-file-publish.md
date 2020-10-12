---
ms.openlocfilehash: 0d6847b7a937094f36efae70ae450cc37824221d
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2020
ms.locfileid: "91955569"
---
### <a name="assembly-related-api-behavior-changes-for-single-file-publishing-format"></a>Tek dosya yayımlama biçimi için derlemeden ilgili API davranışı değişiklikleri

Bir derlemenin dosya konumuyla ilgili birden çok API, tek dosya yayımlama biçiminde çağrıldığında davranış değişikliklerine sahiptir.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET 5,0 ve üzeri sürümler için tek dosya yayımlama sürümünde, paketlenmiş derlemeler diske ayıklanmak yerine bellekten yüklenir. Tek dosya yayımlanan uygulamalar için bu, konum ile ilgili bazı API 'Lerin .NET 5,0 ve üzeri sürümlerde .net 'in önceki sürümlerinden farklı değerler döndürdüğü anlamına gelir. Değişiklikler aşağıdaki gibidir:

| API | Önceki sürümler | .NET 5,0 ve üzeri |
| - | - | - |
| <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> | Ayıklanan DLL dosyası yolunu döndürür | Paketlenmiş derlemeler için boş dize döndürür |
| <xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType> | Ayıklanan DLL dosyası yolunu döndürür | Paketlenmiş derlemeler için özel durum oluşturur |
| <xref:System.Reflection.Assembly.GetFile(System.String)?displayProperty=nameWithType> | `null`Paketlenmiş derlemeler için döndürür | Paketlenmiş derlemeler için özel durum oluşturur |
| `Environment.GetCommandLineArgs()[0]` | Değer, giriş noktası DLL 'inin adıdır | Değer, ana bilgisayarın yürütülebilir dosyasının adıdır |
| <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType> | Değer, geçici ayıklama dizinidir | Değer, ana bilgisayarın yürütülebilir dosyasının bulunduğu dizin |

#### <a name="version-introduced"></a>Sunulan sürüm

5.0

#### <a name="recommended-action"></a>Önerilen eylem

Tek bir dosya olarak yayımlarken derlemelerin dosya konumundaki bağımlılıklardan kaçının.

#### <a name="category"></a>Kategori

- Core .NET kitaplıkları

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.GetFile(System.String)?displayProperty=nameWithType>
- <xref:System.Environment.GetCommandLineArgs?displayProperty=nameWithType>
- <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.Reflection.Assembly.Location`
- `P:System.Reflection.Assembly.CodeBase`
- `M:System.Reflection.Assembly.GetFile(System.String)`
- `M:System.Environment.GetCommandLineArgs`
- `P:System.AppContext.BaseDirectory`

-->
