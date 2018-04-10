---
title: Nesneler (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- objects [Visual Basic]
ms.assetid: 651c73e4-dca8-402b-9c6b-e3902b3a3f4b
caps.latest.revision: 22
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 61c0967521acda8ac3bf8147b817afcf4ca51165
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="objects-visual-basic"></a>Nesneler (Visual Basic)
Bu konu, bu belge Visual Basic çalışma zamanı nesneleri ve onların üyesi yordamları, özellikleri ve olayları tablolar içeren diğer konulara yönelik bağlantılar sağlar.  
  
## <a name="visual-basic-run-time-objects"></a>Visual Basic çalışma zamanı nesneleri  
  
|||  
|---|---|  
|<xref:Microsoft.VisualBasic.Collection>|Tek bir nesne olarak ilgili bir öğe grubunu görmek için kolay bir yol sağlar.|  
|<xref:Microsoft.VisualBasic.Information.Err%2A>|Çalışma zamanı hataları hakkında bilgi içerir.|  
|`My.Application` Nesnesi aşağıdaki sınıflarını içerir:<br /><br /> <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>tüm projelerde kullanılabilir üyeler sağlar.<br /><br /> <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>Windows Forms uygulamalarında kullanılabilir üyeler sağlar.<br /><br /> <xref:Microsoft.VisualBasic.ApplicationServices.ConsoleApplicationBase>konsol uygulamaları kullanılabilir üyeler sağlar.|Yalnızca geçerli uygulama veya DLL ile ilişkili verileri sağlar. Hiçbir sistem düzeyindeki bilgileri ile değiştirilebilir `My.Application`.<br /><br /> Bazı üyeler, yalnızca Windows Forms ya da konsol uygulamaları için kullanılabilir.|  
|`My.Application.Info` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Info%2A>)|Sürüm numarası, açıklama, yüklenen derlemeler ve benzerleri gibi bir uygulama hakkında bilgi almak için özellikleri sağlar.|  
|`My.Application.Log` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log%2A>)|Bir özellik ve olay ve özel durum bilgileri için uygulamanın günlük dinleyicileri yazmak için yöntemler sağlar.|  
|`My.Computer` (<xref:Microsoft.VisualBasic.Devices.Computer>)|Ses, saatin, klavye, dosya sistemi ve benzerleri gibi bilgisayar bileşenlerini yönetmek için gereken özellikleri sağlar.|  
|`My.Computer.Audio` (<xref:Microsoft.VisualBasic.Devices.Audio>)|Ses çalma için yöntemleri sağlar.|  
|`My.Computer.Clipboard` (<xref:Microsoft.VisualBasic.Devices.Computer.Clipboard%2A>)|Pano düzenleme için yöntemleri sağlar.|  
|`My.Computer.Clock` (<xref:Microsoft.VisualBasic.Devices.Clock>)|Geçerli yerel saat ve Evrensel Eşgüdümlü saate (Greenwich saati eşdeğer) sistem saatinden erişmek için özellikleri sağlar.|  
|`My.Computer.FileSystem` (<xref:Microsoft.VisualBasic.FileIO.FileSystem>)|Özellikleri ve sürücüleri, dosyaları ve dizinleri ile çalışmak için yöntemler sağlar.|  
|`My.Computer.FileSystem.SpecialDirectories` (<xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>)|Yaygın olarak erişmek için özellikler dizinleri başvurulan sağlar.|  
|`My.Computer.Info` (<xref:Microsoft.VisualBasic.Devices.ComputerInfo>)|Bilgisayarın bellek, yüklenen derlemeler, ad ve işletim sistemi hakkında bilgi almak için özellikleri sağlar.|  
|`My.Computer.Keyboard` (<xref:Microsoft.VisualBasic.Devices.Keyboard>)|Ne anahtarları şu anda basıldığında ve gibi etkin pencereyi tuş vuruşlarını göndermek için bir yöntem sağlar klavye geçerli durumunu erişmek için özellikleri sağlar.|  
|`My.Computer.Mouse` (<xref:Microsoft.VisualBasic.Devices.Mouse>)|Biçim ve yerel bilgisayarda yüklü fare yapılandırma hakkında bilgi almak için özellikleri sağlar.|  
|`My.Computer.Network` (<xref:Microsoft.VisualBasic.Devices.Network>)|Bir özellik, bir olay ve bilgisayarın bağlı olduğu ağ ile etkileşim için yöntemler sağlar.|  
|`My.Computer.Ports` (<xref:Microsoft.VisualBasic.Devices.Ports>)|Bir özellik ve bilgisayar seri bağlantı noktalarına erişmek için bir yöntem sağlar.|  
|`My.Computer.Registry` (<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>)|Özellikler ve kayıt defterini düzenleme için yöntemler sağlar.|  
|[My.Forms nesnesi](../../../visual-basic/language-reference/objects/my-forms-object.md)|Geçerli projede olarak bildirilen her Windows formunu örneği erişmek için özelliklerde sağlar.|  
|`My.Log` (<xref:Microsoft.VisualBasic.Logging.AspLog>)|Bir özellik ve Web uygulamaları için uygulamanın günlük dinleyicileri olay ve özel durum bilgilerini yazma yöntemleri sağlar.|  
|[My.Request nesnesi](../../../visual-basic/language-reference/objects/my-request-object.md)|Alır <xref:System.Web.HttpRequest> istenen sayfa için nesnesi. `My.Request` Nesnesi geçerli HTTP isteğiyle ilgili bilgileri içerir.<br /><br /> `My.Request` Nesnesidir yalnızca kullanılabilir [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] uygulamalar.|  
|[My.Resources nesnesi](../../../visual-basic/language-reference/objects/my-resources-object.md)|Bir uygulamanın kaynaklara erişmek için özellikleri ve sınıfları sağlar.|  
|[My.Response nesnesi](../../../visual-basic/language-reference/objects/my-response-object.md)|Alır <xref:System.Web.HttpResponse> ile ilişkili nesne <xref:System.Web.UI.Page>. Bu nesne, HTTP yanıt verilerini istemciye göndermenize olanak sağlar ve bu yanıt hakkında bilgi içerir.<br /><br /> `My.Response` Nesnesidir yalnızca kullanılabilir [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] uygulamalar.|  
|[My.Settings nesnesi](../../../visual-basic/language-reference/objects/my-settings-object.md)|Özellikler ve bir uygulamanın ayarlarına erişmek için yöntemler sağlar.|  
|`My.User` (<xref:Microsoft.VisualBasic.ApplicationServices.User>)|Geçerli kullanıcının ilgili bilgilere erişim sağlar.|  
|[My.WebServices nesnesi](../../../visual-basic/language-reference/objects/my-webservices-object.md)|Oluşturma ve erişme geçerli proje tarafından başvurulan her Web hizmeti tek bir örneği için özellikleri sağlar.|  
|<xref:Microsoft.VisualBasic.FileIO.TextFieldParser>|Yapılandırılmış metin ayrıştırmak için yöntemleri ve özellikleri sağlar dosyaları.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic Dil Başvurusu](../../../visual-basic/language-reference/index.md)  
 [Visual Basic](../../../visual-basic/index.md)
