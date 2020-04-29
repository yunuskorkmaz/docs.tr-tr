---
ms.openlocfilehash: c4e7864262a11aafa4b7f1f4bdf632fbf084c560
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507110"
---
### <a name="http-kestrel-and-iis-badhttprequestexception-types-marked-obsolete-and-replaced"></a>HTTP: Kestrel ve IIS BadHttpRequestException türleri artık kullanılmıyor ve değiştirilmiş olarak işaretlendi

`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException`ve `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` artık kullanılmıyor olarak işaretlendi ve öğesinden `Microsoft.AspNetCore.Http.BadHttpRequestException`türetilme değiştirildi. Kestrel ve IIS sunucuları geriye dönük uyumluluk için eski özel durum türlerini hala oluşturur. Eski türler gelecek sürümde kaldırılacak.

Tartışma için bkz. [DotNet/aspnetcore # 20614](https://github.com/dotnet/aspnetcore/issues/20614).

#### <a name="version-introduced"></a>Sunulan sürüm

5,0 Preview 4

#### <a name="old-behavior"></a>Eski davranış

`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException`ve `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` öğesinden <xref:System.IO.IOException?displayProperty=nameWithType>türetilir.

#### <a name="new-behavior"></a>Yeni davranış

`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException`ve `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` artık kullanılmıyor. Türler Ayrıca `Microsoft.AspNetCore.Http.BadHttpRequestException`öğesinden türetilir `System.IO.IOException`.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Değişikliğin yapıldığı yer:

* Yinelenen türleri birleştirin.
* Sunucu uygulamalarında davranışı bütünleştirme.

Uygulama artık Kestrel veya IIS kullanırken temel özel `Microsoft.AspNetCore.Http.BadHttpRequestException` durumu yakalayabilir.

#### <a name="recommended-action"></a>Önerilen eylem

`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` Ve `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` kullanımlarının kullanımlarını ile `Microsoft.AspNetCore.Http.BadHttpRequestException`değiştirin.

#### <a name="category"></a>Kategori

ASP.NET Çekirdeği

#### <a name="affected-apis"></a>Etkilenen API’ler

- [Microsoft. AspNetCore. Server. IIS. BadHttpRequestException](/dotnet/api/microsoft.aspnetcore.server.iis.badhttprequestexception?view=aspnetcore-3.1)
- [Microsoft. AspNetCore. Server. Kestrel. BadHttpRequestException](/dotnet/api/microsoft.aspnetcore.server.kestrel.badhttprequestexception?view=aspnetcore-1.1)

<!--

#### Affected APIs

- `T:Microsoft.AspNetCore.Server.IIS.BadHttpRequestException`
- `T:Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException`

-->
