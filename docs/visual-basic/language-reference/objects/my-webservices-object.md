---
title: My.WebServices Nesnesi
ms.date: 07/20/2015
f1_keywords:
- My.WebServices
- My.MyProject.WebServices
helpviewer_keywords:
- My.WebServices object
ms.assetid: f188dc05-2c75-41b6-bb68-122d1c3110a2
ms.openlocfilehash: 290d025985663bc45fe605a2e9904fc90fb2bc63
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350343"
---
# <a name="mywebservices-object"></a>My.WebServices Nesnesi
Geçerli proje tarafından başvurulan her bir XML Web hizmetinin tek bir örneğini oluşturmaya ve bunlara erişmeye yönelik özellikler sağlar.  
  
## <a name="remarks"></a>Açıklamalar  
 `My.WebServices` nesnesi, geçerli proje tarafından başvurulan her bir Web hizmetinin örneğini sağlar. Her örnek isteğe bağlı olarak oluşturulur. Bu Web hizmetlerine `My.WebServices` nesnesinin özellikleri aracılığıyla erişebilirsiniz. Özelliğin adı, özelliğin eriştiği Web hizmetinin adıyla aynıdır. <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> devralan tüm sınıflar bir Web hizmetidir. Bir projeye Web Hizmetleri ekleme hakkında daha fazla bilgi için bkz. [uygulama Web Hizmetleri 'Ne erişme](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).  
  
 `My.WebServices` nesnesi yalnızca geçerli projeyle ilişkili Web hizmetlerini kullanıma sunar. Başvurulan DLL 'lerde belirtilen Web hizmetlerine erişim sağlamaz. Bir DLL 'nin sağladığı bir Web hizmetine erişmek için, Web hizmeti 'nin adı *dlladı*biçiminde kullanmanız gerekir. *WebServiceName*. Daha fazla bilgi için bkz. [uygulama Web Hizmetleri 'Ne erişme](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).  
  
 Nesne ve özellikleri Web uygulamaları için kullanılamaz.  
  
## <a name="properties"></a>Özellikler  
 `My.WebServices` nesnesinin her özelliği, geçerli proje tarafından başvurulan bir Web hizmeti örneğine erişim sağlar. Özelliğin adı, özelliğin eriştiği Web hizmeti adı ile aynıdır ve özellik türü, Web hizmetinin türüyle aynıdır.  
  
> [!NOTE]
> Bir ad çakışması varsa, bir Web hizmetine erişmek için özellik adı *,\_* *ServiceName*ad *alanıdır*. Örneğin, `Service1`adlı iki Web hizmeti göz önünde bulundurun. Bu hizmetlerden biri kök ad alanında `WindowsApplication1` ve ad alanı `Namespace1`, bu hizmete `My.WebServices.WindowsApplication1_Namespace1_Service1`kullanarak erişirsiniz.  
  
 `My.WebServices` nesnesinin özelliklerinden birine ilk kez eriştiğinizde, Web hizmetinin yeni bir örneğini oluşturur ve depolar. Bu özelliğin sonraki erişimleri, Web hizmetinin bu örneğini döndürür.  
  
 Web hizmetini, bu Web hizmetinin özelliğine `Nothing` atayarak atabilirsiniz. Özellik ayarlayıcısı `Nothing` depolanan değere atar. Özelliğe `Nothing` dışında herhangi bir değer atarsanız, ayarlayıcı bir <xref:System.ArgumentException> özel durumu oluşturur.  
  
 `My.WebServices` nesnesinin bir özelliğinin bir Web hizmeti örneğini `Is` veya `IsNot` işlecini kullanarak depolayıp depoladığını test edebilirsiniz. Bu işleçleri, özelliğin değerinin `Nothing`olup olmadığını denetlemek için kullanabilirsiniz.  
  
> [!NOTE]
> Genellikle, `Is` veya `IsNot` işleci, karşılaştırmayı gerçekleştirmek için özelliğinin değerini okumalı. Ancak, özelliği şu anda `Nothing`depoluyorsa, özelliği Web hizmetinin yeni bir örneğini oluşturur ve ardından bu örneği döndürür. Ancak Visual Basic derleyici, `My.WebServices` nesnesinin özelliklerini özel olarak değerlendirir ve `Is` ya da `IsNot` işlecinin değerini değiştirmeden özelliğin durumunu denetlemesini sağlar.  
  
## <a name="example"></a>Örnek  
 Bu örnek, `TemperatureConverter` XML Web hizmetinin `FahrenheitToCelsius` yöntemini çağırır ve sonucu döndürür.  
  
 [!code-vb[VbVbalrMyWebService#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWebService/VB/Form1.vb#1)]  
  
 Bu örneğin çalışması için, projenizin `Converter`adlı bir Web hizmetine başvurması gerekir ve bu Web hizmeti `ConvertTemperature` yöntemini kullanıma sunmalıdır. Daha fazla bilgi için bkz. [uygulama Web Hizmetleri 'Ne erişme](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).  
  
 Bu kod, bir Web uygulaması projesinde çalışmaz.  
  
## <a name="requirements"></a>Gereksinimler  
  
### <a name="availability-by-project-type"></a>Proje Türüne Göre Kullanılabilirlik  
  
|Proje türü|Kullanılabilir|  
|---|---|  
|Windows uygulaması|**Yes**|  
|Sınıf Kitaplığı|**Yes**|  
|Konsol Uygulaması|**Yes**|  
|Windows Denetim Kitaplığı|**Yes**|  
|Web Denetim Kitaplığı|**Yes**|  
|Windows Hizmeti|**Yes**|  
|Web Sitesi|Hayır|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Web.Services.Protocols.SoapHttpClientProtocol>
- <xref:System.ArgumentException>
- [Uygulama Web Hizmetlerine Erişme](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)
