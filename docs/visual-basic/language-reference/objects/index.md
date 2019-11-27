---
title: Nesneler
ms.date: 07/20/2015
helpviewer_keywords:
- objects [Visual Basic]
ms.assetid: 651c73e4-dca8-402b-9c6b-e3902b3a3f4b
ms.openlocfilehash: 8956d8dd8f46b4235d71802ccc743dfebcb051be
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344152"
---
# <a name="objects-visual-basic"></a>Nesneler (Visual Basic)
Bu konu, Visual Basic çalışma zamanı nesnelerini belgelemek ve üye yordamlarının, özelliklerinin ve olaylarının tablolarını içeren diğer konulara bağlantılar sağlar.  
  
## <a name="visual-basic-run-time-objects"></a>Çalışma zamanı nesneleri Visual Basic  
  
|||  
|---|---|  
|<xref:Microsoft.VisualBasic.Collection>|İlgili öğe grubunu tek bir nesne olarak görmek için kullanışlı bir yol sağlar.|  
|<xref:Microsoft.VisualBasic.Information.Err%2A>|Çalışma zamanı hatalarıyla ilgili bilgileri içerir.|  
|`My.Application` nesnesi aşağıdaki sınıflardan oluşur:<br /><br /> <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase> tüm projelerde kullanılabilen üyeleri sağlar.<br /><br /> <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>, Windows Forms uygulamalarda bulunan üyeleri sağlar.<br /><br /> <xref:Microsoft.VisualBasic.ApplicationServices.ConsoleApplicationBase>, konsol uygulamalarında kullanılabilir üyeleri sağlar.|Yalnızca geçerli uygulama veya DLL ile ilişkili olan verileri sağlar. `My.Application`ile hiçbir sistem düzeyi bilgi değiştirilemez.<br /><br /> Bazı üyeler yalnızca Windows Forms veya konsol uygulamaları için kullanılabilir.|  
|`My.Application.Info` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Info%2A>)|Sürüm numarası, açıklama, yüklenen derlemeler vb. gibi bir uygulamayla ilgili bilgilerin alınması için özellikler sağlar.|  
|`My.Application.Log` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log%2A>)|Uygulamanın günlük dinleyicilerine olay ve özel durum bilgilerini yazmak için bir özellik ve yöntemler sağlar.|  
|`My.Computer` (<xref:Microsoft.VisualBasic.Devices.Computer>)|Ses, saat, klavye, dosya sistemi vb. gibi bilgisayar bileşenlerinin işlenmesine yönelik özellikler sağlar.|  
|`My.Computer.Audio` (<xref:Microsoft.VisualBasic.Devices.Audio>)|Ses çalmak için yöntemler sağlar.|  
|`My.Computer.Clipboard` (<xref:Microsoft.VisualBasic.Devices.Computer.Clipboard%2A>)|Panoyu işlemek için yöntemler sağlar.|  
|`My.Computer.Clock` (<xref:Microsoft.VisualBasic.Devices.Clock>)|Geçerli yerel saate ve Evrensel Eşgüdümlü saate (Greenwich Ortalama Saati ile eşdeğer) sistem saatinden erişilmesine yönelik özellikler sağlar.|  
|`My.Computer.FileSystem` (<xref:Microsoft.VisualBasic.FileIO.FileSystem>)|Sürücüler, dosyalar ve dizinler ile çalışmaya yönelik özellikler ve yöntemler sağlar.|  
|`My.Computer.FileSystem.SpecialDirectories` (<xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>)|Yaygın olarak başvurulan dizinlere erişim özellikleri sağlar.|  
|`My.Computer.Info` (<xref:Microsoft.VisualBasic.Devices.ComputerInfo>)|Bilgisayarın belleği, yüklü derlemeler, ad ve işletim sistemi hakkında bilgi almak için özellikler sağlar.|  
|`My.Computer.Keyboard` (<xref:Microsoft.VisualBasic.Devices.Keyboard>)|Klavyenin geçerli durumuna erişim için özellikler sağlar, örneğin, şu anda basılan anahtarlar ve etkin pencereye tuş vuruşları göndermek için bir yöntem sağlar.|  
|`My.Computer.Mouse` (<xref:Microsoft.VisualBasic.Devices.Mouse>)|Yerel bilgisayarda yüklü olan farenin biçimi ve yapılandırması hakkında bilgi almak için özellikler sağlar.|  
|`My.Computer.Network` (<xref:Microsoft.VisualBasic.Devices.Network>)|Bilgisayarın bağlı olduğu ağla etkileşimde bulunmak için bir özellik, olay ve yöntemler sağlar.|  
|`My.Computer.Ports` (<xref:Microsoft.VisualBasic.Devices.Ports>)|Bilgisayarın seri bağlantı noktalarına erişmek için bir özellik ve bir yöntem sağlar.|  
|`My.Computer.Registry` (<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>)|Kayıt defterini işlemek için özellikler ve yöntemler sağlar.|  
|[My.Forms Nesnesi](../../../visual-basic/language-reference/objects/my-forms-object.md)|Geçerli projede belirtilen her bir Windows formunun örneğine erişim için özellikler sağlar.|  
|`My.Log` (<xref:Microsoft.VisualBasic.Logging.AspLog>)|Web uygulamaları için uygulamanın günlük dinleyicilerine olay ve özel durum bilgilerini yazmak için bir özellik ve yöntemler sağlar.|  
|[My.Request Nesnesi](../../../visual-basic/language-reference/objects/my-request-object.md)|İstenen sayfa için <xref:System.Web.HttpRequest> nesnesini alır. `My.Request` nesnesi geçerli HTTP isteğiyle ilgili bilgiler içerir.<br /><br /> `My.Request` nesnesi yalnızca ASP.NET uygulamaları için kullanılabilir.|  
|[My.Resources Nesnesi](../../../visual-basic/language-reference/objects/my-resources-object.md)|Uygulamanın kaynaklarına erişmek için özellikler ve sınıflar sağlar.|  
|[My.Response Nesnesi](../../../visual-basic/language-reference/objects/my-response-object.md)|<xref:System.Web.UI.Page>ilişkili <xref:System.Web.HttpResponse> nesnesini alır. Bu nesne bir istemciye HTTP yanıt verileri göndermenizi ve bu yanıt hakkındaki bilgileri eklemenizi sağlar.<br /><br /> `My.Response` nesnesi yalnızca ASP.NET uygulamaları için kullanılabilir.|  
|[My.Settings Nesnesi](../../../visual-basic/language-reference/objects/my-settings-object.md)|Uygulamanın ayarlarına erişmek için özellikler ve yöntemler sağlar.|  
|`My.User` (<xref:Microsoft.VisualBasic.ApplicationServices.User>)|Geçerli kullanıcı hakkındaki bilgilere erişim sağlar.|  
|[My.WebServices Nesnesi](../../../visual-basic/language-reference/objects/my-webservices-object.md)|Geçerli proje tarafından başvurulan her bir Web hizmetinin tek bir örneğini oluşturmaya ve bunlara erişmeye yönelik özellikler sağlar.|  
|<xref:Microsoft.VisualBasic.FileIO.TextFieldParser>|Yapılandırılmış metin dosyalarını ayrıştırmak için yöntemler ve özellikler sağlar.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic Dili Başvurusu](../../../visual-basic/language-reference/index.md)
- [Visual Basic](../../../visual-basic/index.md)
