---
title: Nesneler
ms.date: 07/20/2015
helpviewer_keywords:
- objects [Visual Basic]
ms.assetid: 651c73e4-dca8-402b-9c6b-e3902b3a3f4b
ms.openlocfilehash: e927f69b7606866a0a9e8eadd59270f51ffc5e2b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414225"
---
# <a name="objects-visual-basic"></a>Nesneler (Visual Basic)
Bu konu, Visual Basic çalışma zamanı nesnelerini belgelemek ve üye yordamlarının, özelliklerinin ve olaylarının tablolarını içeren diğer konulara bağlantılar sağlar.  
  
## <a name="visual-basic-run-time-objects"></a>Çalışma zamanı nesneleri Visual Basic  
  
|||  
|---|---|  
|<xref:Microsoft.VisualBasic.Collection>|İlgili öğe grubunu tek bir nesne olarak görmek için kullanışlı bir yol sağlar.|  
|<xref:Microsoft.VisualBasic.Information.Err%2A>|Çalışma zamanı hatalarıyla ilgili bilgileri içerir.|  
|`My.Application`Nesnesi aşağıdaki sınıflardan oluşur:<br /><br /> <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>tüm projelerde kullanılabilen üyeleri sağlar.<br /><br /> <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>Windows Forms uygulamalarında kullanılabilir üyeleri sağlar.<br /><br /> <xref:Microsoft.VisualBasic.ApplicationServices.ConsoleApplicationBase>Konsol uygulamalarında kullanılabilir üyeleri sağlar.|Yalnızca geçerli uygulama veya DLL ile ilişkili olan verileri sağlar. İle hiçbir sistem düzeyi bilgisi değiştirilemez `My.Application` .<br /><br /> Bazı üyeler yalnızca Windows Forms veya konsol uygulamaları için kullanılabilir.|  
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
|[My.Forms Nesnesi](my-forms-object.md)|Geçerli projede belirtilen her bir Windows formunun örneğine erişim için özellikler sağlar.|  
|`My.Log` (<xref:Microsoft.VisualBasic.Logging.AspLog>)|Web uygulamaları için uygulamanın günlük dinleyicilerine olay ve özel durum bilgilerini yazmak için bir özellik ve yöntemler sağlar.|  
|[My.Request Nesnesi](my-request-object.md)|<xref:System.Web.HttpRequest>İstenen sayfa için nesneyi alır. `My.Request`Nesne, GEÇERLI HTTP isteğiyle ilgili bilgiler içerir.<br /><br /> `My.Request`Nesne yalnızca ASP.NET uygulamaları için kullanılabilir.|  
|[My.Resources Nesnesi](my-resources-object.md)|Uygulamanın kaynaklarına erişmek için özellikler ve sınıflar sağlar.|  
|[My.Response Nesnesi](my-response-object.md)|<xref:System.Web.HttpResponse>İle ilişkili nesneyi alır <xref:System.Web.UI.Page> . Bu nesne bir istemciye HTTP yanıt verileri göndermenizi ve bu yanıt hakkındaki bilgileri eklemenizi sağlar.<br /><br /> `My.Response`Nesne yalnızca ASP.NET uygulamaları için kullanılabilir.|  
|[My.Settings Nesnesi](my-settings-object.md)|Uygulamanın ayarlarına erişmek için özellikler ve yöntemler sağlar.|  
|`My.User` (<xref:Microsoft.VisualBasic.ApplicationServices.User>)|Geçerli kullanıcı hakkındaki bilgilere erişim sağlar.|  
|[My.WebServices Nesnesi](my-webservices-object.md)|Geçerli proje tarafından başvurulan her bir Web hizmetinin tek bir örneğini oluşturmaya ve bunlara erişmeye yönelik özellikler sağlar.|  
|<xref:Microsoft.VisualBasic.FileIO.TextFieldParser>|Yapılandırılmış metin dosyalarını ayrıştırmak için yöntemler ve özellikler sağlar.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic dil başvurusu](../index.md)
