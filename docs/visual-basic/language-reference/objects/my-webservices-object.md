---
title: My.WebServices Nesnesi
ms.date: 07/20/2015
f1_keywords:
- My.WebServices
- My.MyProject.WebServices
helpviewer_keywords:
- My.WebServices object
ms.assetid: f188dc05-2c75-41b6-bb68-122d1c3110a2
ms.openlocfilehash: 9519638c7609b9b1d0f5e07397c46975e2696c94
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="mywebservices-object"></a>My.WebServices Nesnesi
Oluşturma ve erişme geçerli proje tarafından başvurulan her XML Web hizmetinin tek bir örneği için özellikleri sağlar.  
  
## <a name="remarks"></a>Açıklamalar  
 `My.WebServices` Nesnesi geçerli proje tarafından başvurulan her Web hizmeti örneğini sağlar. İsteğe bağlı olarak her bir örnek örneği. Bu Web Hizmetleri özelliklerini erişebilirsiniz `My.WebServices` nesnesi. Özelliğin adını özelliğe erişir Web hizmeti adı ile aynıdır. Öğesinden devralınan herhangi bir sınıf <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> bir Web hizmetidir. Web Hizmetleri için bir proje ekleme hakkında daha fazla bilgi için bkz: [uygulama Web hizmetlerine erişme](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).  
  
 `My.WebServices` Nesne yalnızca geçerli projeyle ilişkili Web hizmetleri sunar. Başvurulan DLL'lerde bildirilen Web hizmetlerine erişim sağlamaz. DLL sağlayan bir Web hizmetine erişmek için Web hizmeti tam adı biçiminde kullanmalısınız *dll*. *WebServiceName*. Daha fazla bilgi için bkz: [uygulama Web hizmetlerine erişme](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).  
  
 Nesne ve özelliklerini Web uygulamaları için kullanılabilir değil.  
  
## <a name="properties"></a>Özellikler  
 Her bir özelliğinin `My.WebServices` nesne geçerli proje tarafından başvurulan bir Web hizmeti örneğine erişim sağlar. Özelliğin adını özelliğe erişir Web hizmeti adı ile aynıdır ve özellik türü Web Service'in türü ile aynıdır.  
  
> [!NOTE]
>  Bir ad çakışması varsa, Web hizmetine erişim için özellik adı olan *RootNamespace*_*Namespace*\_*ServiceName*. Örneğin, adında iki Web Hizmetleri göz önünde bulundurun `Service1`. Bu hizmetlerden biri kök ad alanını olup olmadığını `WindowsApplication1` ve ad alanında `Namespace1`, kullanarak bu hizmeti erişir `My.WebServices.WindowsApplication1_Namespace1_Service1`.  
  
 İlk eriştiğinizde birini `My.WebServices` nesnenin özelliklerini, Web hizmetinin yeni bir örneğini oluşturur ve depolar. Bu özelliğin sonraki erişimleri Web hizmeti örneğini döndürür.  
  
 Bir Web hizmeti atayarak dispose `Nothing` özelliğine bu Web hizmeti. Özellik ayarlayıcısı atar `Nothing` depolanan değer. Herhangi bir değer dışındaki atarsanız `Nothing` özelliğine kurucu oluşturur bir <xref:System.ArgumentException> özel durum.  
  
 Bir özelliği olup olmadığını sınayabilirsiniz `My.WebServices` nesnesini kullanarak Web hizmetinin bir örneğini depolar `Is` veya `IsNot` işleci. Özelliğinin değeri olup olmadığını denetlemek için bu işleçleri kullanabilirsiniz `Nothing`.  
  
> [!NOTE]
>  Genellikle, `Is` veya `IsNot` sahip karşılaştırma yapabilmesi için özellik değeri okunamıyor. Ancak, özelliği şu anda depoluyorsa `Nothing`, özelliğin Web hizmetini yeni bir örneğini oluşturur ve o örneği döndürür. Ancak, Visual Basic derleyici özelliklerini değerlendirir `My.WebServices` özel nesne ve verir `Is` veya `IsNot` değerini değiştirmeden özelliği durumunu denetlemek için işleci.  
  
## <a name="example"></a>Örnek  
 Bu örnek çağırır `FahrenheitToCelsius` yöntemi `TemperatureConverter` XML Web hizmeti ve sonucu döndürür.  
  
 [!code-vb[VbVbalrMyWebService#1](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-webservices-object_1.vb)]  
  
 Bu örnek çalışmaya adlı bir Web hizmeti projenizi başvurmalıdır `Converter`, ve bu Web hizmeti kullanıma gerekir `ConvertTemperature` yöntemi. Daha fazla bilgi için bkz: [uygulama Web hizmetlerine erişme](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).  
  
 Bu kod, bir Web uygulaması projesi çalışmaz.  
  
## <a name="requirements"></a>Gereksinimler  
  
### <a name="availability-by-project-type"></a>Proje Türüne Göre Kullanılabilirlik  
  
|Proje türü|Kullanılabilir|  
|---|---|  
|Windows uygulaması|**Evet**|  
|Sınıf Kitaplığı|**Evet**|  
|Konsol Uygulaması|**Evet**|  
|Windows Denetim Kitaplığı|**Evet**|  
|Web Denetim Kitaplığı|**Evet**|  
|Windows Hizmeti|**Evet**|  
|Web Sitesi|Hayır|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Web.Services.Protocols.SoapHttpClientProtocol>  
 <xref:System.ArgumentException>  
 [Uygulama Web Hizmetlerine Erişme](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)
