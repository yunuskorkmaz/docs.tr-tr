---
title: Nesneler (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- objects [Visual Basic]
ms.assetid: 651c73e4-dca8-402b-9c6b-e3902b3a3f4b
ms.openlocfilehash: 59558583a35f83baa953cfc94a17c6c002f91b83
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54703503"
---
# <a name="objects-visual-basic"></a>Nesneler (Visual Basic)
Bu konu, bu belge, Visual Basic çalışma zamanı nesneleri ve tablolar, üye yordamları, özellikleri ve olayları içeren diğer konulara bağlantılar sağlar.  
  
## <a name="visual-basic-run-time-objects"></a>Visual Basic çalışma zamanı nesneleri  
  
|||  
|---|---|  
|<xref:Microsoft.VisualBasic.Collection>|Tek bir nesne olarak ilgili bir öğe grubunu görmek için kullanışlı bir yol sağlar.|  
|<xref:Microsoft.VisualBasic.Information.Err%2A>|Çalışma zamanı hataları hakkında bilgi içerir.|  
|`My.Application` Nesnesi aşağıdaki sınıfları içerir:<br /><br /> <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase> tüm projelerde kullanılabilen üyeleri sağlar.<br /><br /> <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> Windows Forms uygulamalarında kullanılabilir üyeleri sağlar.<br /><br /> <xref:Microsoft.VisualBasic.ApplicationServices.ConsoleApplicationBase> Konsol uygulamalarında kullanılabilir üyeleri sağlar.|Yalnızca geçerli uygulama veya DLL ile ilişkili veriler sağlar. Hiçbir sistem düzeyindeki bilgileri ile değiştirilebilir `My.Application`.<br /><br /> Bazı üyeler, yalnızca Windows Forms veya konsol uygulamaları için kullanılabilir.|  
|`My.Application.Info` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Info%2A>)|Sürüm numarası, açıklama, yüklenen derlemeler ve benzeri gibi bir uygulamayla ilgili bilgileri almak için özellikleri sağlar.|  
|`My.Application.Log` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log%2A>)|Bir özellik ve olay ve özel durum bilgileri için uygulamanın günlük dinleyicileri yazmak için yöntemler sağlar.|  
|`My.Computer` (<xref:Microsoft.VisualBasic.Devices.Computer>)|Ses, saat, klavye, dosya sistemi ve benzeri gibi bilgisayar bileşenlerini yönetmek için gereken özellikleri sağlar.|  
|`My.Computer.Audio` (<xref:Microsoft.VisualBasic.Devices.Audio>)|Ses çalma için yöntemler sağlar.|  
|`My.Computer.Clipboard` (<xref:Microsoft.VisualBasic.Devices.Computer.Clipboard%2A>)|Pano yönlendirmeye yönelik yöntemleri sağlar.|  
|`My.Computer.Clock` (<xref:Microsoft.VisualBasic.Devices.Clock>)|Geçerli yerel saat ve Eşgüdümlü Evrensel Saat (Greenwich saati ile eşdeğerdir), sistem saatinden erişmek için özellikleri sağlar.|  
|`My.Computer.FileSystem` (<xref:Microsoft.VisualBasic.FileIO.FileSystem>)|Özellikler ve sürücüleri, dosyalar ve dizinler ile çalışmak için yöntemler sağlar.|  
|`My.Computer.FileSystem.SpecialDirectories` (<xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>)|Yaygın olarak erişmek için özellikler dizinleri başvurulan sağlar.|  
|`My.Computer.Info` (<xref:Microsoft.VisualBasic.Devices.ComputerInfo>)|Bilgisayarın bellek, yüklenen derlemeler, ad ve işletim sistemi hakkında bilgi almak için özellikleri sağlar.|  
|`My.Computer.Keyboard` (<xref:Microsoft.VisualBasic.Devices.Keyboard>)|Geçerli durumu ne anahtarları şu anda basıldığında ve gönderme tuş vuruşları etkin pencereyi bir yöntem sağlar klavye ile erişmek için özellikleri sağlar.|  
|`My.Computer.Mouse` (<xref:Microsoft.VisualBasic.Devices.Mouse>)|Biçim ve yerel bilgisayarda yüklü olan fare yapılandırma hakkında bilgi almak için özellikleri sağlar.|  
|`My.Computer.Network` (<xref:Microsoft.VisualBasic.Devices.Network>)|Bir özellik, bir olay ve bilgisayarın bağlı olduğu ağ ile etkileşim için yöntemler sağlar.|  
|`My.Computer.Ports` (<xref:Microsoft.VisualBasic.Devices.Ports>)|Bir özellik ve bilgisayar ile seri bağlantı noktalarına erişmek için bir yöntem sağlar.|  
|`My.Computer.Registry` (<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>)|Özellikler ve kayıt defterini düzenlemek için yöntemler sağlar.|  
|[My.Forms Nesnesi](../../../visual-basic/language-reference/objects/my-forms-object.md)|Her Windows formunu örneğini erişmeye yönelik özellikler geçerli projedeki bildirilen sağlar.|  
|`My.Log` (<xref:Microsoft.VisualBasic.Logging.AspLog>)|Bir özellik ve Web uygulamaları için uygulamanın günlük dinleyicileri için olay ve özel durum bilgilerini yazma yöntemleri sağlar.|  
|[My.Request Nesnesi](../../../visual-basic/language-reference/objects/my-request-object.md)|Alır <xref:System.Web.HttpRequest> istenen sayfa nesnesi. `My.Request` Nesnesi geçerli HTTP isteğiyle ilgili bilgileri içerir.<br /><br /> `My.Request` Yalnızca nesne kullanılabilir [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] uygulamalar.|  
|[My.Resources Nesnesi](../../../visual-basic/language-reference/objects/my-resources-object.md)|Bir uygulamanın kaynaklara erişmek için özellikler ve sınıfları sağlar.|  
|[My.Response Nesnesi](../../../visual-basic/language-reference/objects/my-response-object.md)|Alır <xref:System.Web.HttpResponse> ile ilişkili nesne <xref:System.Web.UI.Page>. Bu nesne, HTTP yanıt verilerini istemciye göndermenize olanak sağlar ve bu yanıt hakkında bilgiler içerir.<br /><br /> `My.Response` Yalnızca nesne kullanılabilir [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] uygulamalar.|  
|[My.Settings Nesnesi](../../../visual-basic/language-reference/objects/my-settings-object.md)|Özellikler ve uygulama ayarlarına erişme için yöntemler sağlar.|  
|`My.User` (<xref:Microsoft.VisualBasic.ApplicationServices.User>)|Geçerli kullanıcı ile ilgili bilgilere erişim sağlar.|  
|[My.WebServices Nesnesi](../../../visual-basic/language-reference/objects/my-webservices-object.md)|Oluşturma ve erişme geçerli proje tarafından başvurulan her Web hizmeti tek bir örneği için özellikleri sağlar.|  
|<xref:Microsoft.VisualBasic.FileIO.TextFieldParser>|Yapılandırılmış metin ayrıştırmak için yöntemler ve özellikler sağlar. dosyaları.|  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Visual Basic Dili Başvurusu](../../../visual-basic/language-reference/index.md)
- [Visual Basic](../../../visual-basic/index.md)
