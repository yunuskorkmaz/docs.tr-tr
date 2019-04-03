---
title: My.WebServices nesnesi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.WebServices
- My.MyProject.WebServices
helpviewer_keywords:
- My.WebServices object
ms.assetid: f188dc05-2c75-41b6-bb68-122d1c3110a2
ms.openlocfilehash: a60f32c4f581e42f240fca55ce496776c5511ba3
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58840438"
---
# <a name="mywebservices-object"></a>My.WebServices Nesnesi
Oluşturma ve erişme geçerli proje tarafından başvurulan her bir XML Web hizmeti tek bir örneği için özellikleri sağlar.  
  
## <a name="remarks"></a>Açıklamalar  
 `My.WebServices` Nesnesi, geçerli proje tarafından başvurulan her Web Hizmeti'nin bir örneğini sağlar. Her örnek isteğe bağlı olarak başlatılır. Özellikleri kullanılarak bu Web hizmetlerine erişebilir `My.WebServices` nesne. Özelliğin adı, özellik erişen bir Web hizmeti adı ile aynıdır. Devralınan herhangi bir sınıf <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> bir Web hizmetidir. Bir projeye Web Hizmetleri ekleme hakkında daha fazla bilgi için bkz: [uygulama Web hizmetlerine erişme](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).  
  
 `My.WebServices` Nesnesi geçerli projeyle ilişkili Web Hizmetleri kullanıma sunar. DLL içinde bildirilen Web hizmetlerine erişim sağlamaz. Bir DLL sağlayan bir Web hizmetine erişmek için Web hizmeti tam adı biçiminde kullanmalısınız *dll*. *WebServiceName*. Daha fazla bilgi için [uygulama Web hizmetlerine erişme](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).  
  
 Nesne ve özelliklerini, Web uygulamaları için kullanılamaz.  
  
## <a name="properties"></a>Özellikler  
 Her bir özelliği `My.WebServices` nesnesi geçerli proje tarafından başvurulan bir Web hizmeti örneğine erişim sağlar. Özelliğin adı özelliği erişen bir Web hizmeti adı ile aynıdır ve özellik türü Web hizmetinin türü ile aynıdır.  
  
> [!NOTE]
>  Bir ad çakışması varsa, Web hizmetine erişim için özellik adı olan *RootNamespace*_*Namespace*\_*ServiceName*. Örneğin, adında iki Web Hizmetleri düşünün `Service1`. Bu hizmetlerden biri kök ad alanında olup olmadığını `WindowsApplication1` ve ad alanındaki `Namespace1`, bu hizmeti kullanarak erişir `My.WebServices.WindowsApplication1_Namespace1_Service1`.  
  
 İlk kez eriştiğinizde birini `My.WebServices` nesnenin özelliklerini bu Web hizmetini yeni bir örneğini oluşturur ve depolar. Bu özelliğin sonraki erişir, Web hizmeti örneğini döndürür.  
  
 Bir Web hizmeti atayarak dispose `Nothing` özelliğine, Web hizmeti. Özellik ayarlayıcısını atar `Nothing` depolanmış değere. Dışında herhangi bir değer atamanız durumunda `Nothing` ayarlayıcı özelliğine atar bir <xref:System.ArgumentException> özel durum.  
  
 Bir özelliği olup olmadığını sınayabilirsiniz `My.WebServices` nesnesi kullanarak Web Hizmeti'nin bir örneğini depolar `Is` veya `IsNot` işleci. Bu işleçler özelliğinin değeri olup olmadığını denetlemek için kullanabileceğiniz `Nothing`.  
  
> [!NOTE]
>  Genellikle, `Is` veya `IsNot` işleci olan bir karşılaştırma yapmak için özelliğinin değeri okunamıyor. Ancak, bu özellik şu anda depoluyorsa `Nothing`, özelliği, Web hizmetini yeni bir örneğini oluşturur ve bu örneği döndürür. Ancak, Visual Basic derleyici özelliklerini işler `My.WebServices` özel nesne ve verir `Is` veya `IsNot` değerini değiştirmeden özelliğinin durumu denetlemek için işleci.  
  
## <a name="example"></a>Örnek  
 Bu örnek `FahrenheitToCelsius` yöntemi `TemperatureConverter` XML Web hizmeti ve sonucu döndürür.  
  
 [!code-vb[VbVbalrMyWebService#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWebService/VB/Form1.vb#1)]  
  
 Bu örneğin çalışması, projenizi adlı bir Web hizmeti başvurmalıdır `Converter`, ve bu Web hizmetini kullanıma sunması gerekir `ConvertTemperature` yöntemi. Daha fazla bilgi için [uygulama Web hizmetlerine erişme](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).  
  
 Bu kod, bir Web uygulaması projesinde çalışmaz.  
  
## <a name="requirements"></a>Gereksinimler  
  
### <a name="availability-by-project-type"></a>Proje Türüne Göre Kullanılabilirlik  
  
|Proje türü|Kullanılabilir|  
|---|---|  
|Windows uygulama|**Evet**|  
|Sınıf Kitaplığı|**Evet**|  
|Konsol Uygulaması|**Evet**|  
|Windows Denetim Kitaplığı|**Evet**|  
|Web Denetim Kitaplığı|**Evet**|  
|Windows Hizmeti|**Evet**|  
|Web Sitesi|Hayır|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Web.Services.Protocols.SoapHttpClientProtocol>
- <xref:System.ArgumentException>
- [Uygulama Web Hizmetlerine Erişme](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)
