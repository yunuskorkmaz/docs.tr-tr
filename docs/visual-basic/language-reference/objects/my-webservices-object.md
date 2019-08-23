---
title: My. WebServices nesnesi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.WebServices
- My.MyProject.WebServices
helpviewer_keywords:
- My.WebServices object
ms.assetid: f188dc05-2c75-41b6-bb68-122d1c3110a2
ms.openlocfilehash: c887f9b7c5a41c0aa02016354c46d5507b103d25
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918174"
---
# <a name="mywebservices-object"></a>My.WebServices Nesnesi
Geçerli proje tarafından başvurulan her bir XML Web hizmetinin tek bir örneğini oluşturmaya ve bunlara erişmeye yönelik özellikler sağlar.  
  
## <a name="remarks"></a>Açıklamalar  
 `My.WebServices` Nesnesi, geçerli proje tarafından başvurulan her bir Web hizmetinin örneğini sağlar. Her örnek isteğe bağlı olarak oluşturulur. Bu Web hizmetlerine `My.WebServices` nesnenin özellikleri aracılığıyla erişebilirsiniz. Özelliğin adı, özelliğin eriştiği Web hizmetinin adıyla aynıdır. Öğesinden <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> devralan tüm sınıflar bir Web hizmetidir. Bir projeye Web Hizmetleri ekleme hakkında daha fazla bilgi için bkz. [uygulama Web Hizmetleri 'Ne erişme](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).  
  
 `My.WebServices` Nesne yalnızca geçerli projeyle ilişkili Web hizmetlerini kullanıma sunar. Başvurulan DLL 'lerde belirtilen Web hizmetlerine erişim sağlamaz. Bir DLL 'nin sağladığı bir Web hizmetine erişmek için, Web hizmeti 'nin adı *dlladı*biçiminde kullanmanız gerekir. *WebServiceName*. Daha fazla bilgi için bkz. [uygulama Web Hizmetleri 'Ne erişme](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).  
  
 Nesne ve özellikleri Web uygulamaları için kullanılamaz.  
  
## <a name="properties"></a>Özellikler  
 `My.WebServices` Nesnesinin her özelliği, geçerli proje tarafından başvurulan bir Web hizmeti örneğine erişim sağlar. Özelliğin adı, özelliğin eriştiği Web hizmeti adı ile aynıdır ve özellik türü, Web hizmetinin türüyle aynıdır.  
  
> [!NOTE]
> Ad çakışması varsa, bir Web hizmetine erişmek için özellik adı *RootNamespace*_*ad*\_alanı*HizmetAdı*olur. Örneğin, adlı `Service1`iki Web hizmeti göz önünde bulundurun. Bu hizmetlerden biri kök ad alanında `WindowsApplication1` ve ad `Namespace1`alanında ise, kullanarak `My.WebServices.WindowsApplication1_Namespace1_Service1`bu hizmete erişirsiniz.  
  
 `My.WebServices` Nesnenin özelliklerinden birine ilk kez eriştiğinizde, Web hizmetinin yeni bir örneğini oluşturur ve depolar. Bu özelliğin sonraki erişimleri, Web hizmetinin bu örneğini döndürür.  
  
 Bu Web hizmeti için özelliğine atayarak `Nothing` bir Web hizmetini atabilirsiniz. Özellik ayarlayıcısı saklı değere `Nothing` atar. Özelliği dışında bir değer `Nothing` atarsanız, ayarlayıcı bir <xref:System.ArgumentException> özel durum oluşturur.  
  
 Bir `My.WebServices` nesnenin özelliğinin, `Is` veya `IsNot` işlecini kullanarak bir Web hizmeti örneğini depolayıp depomadığını test edebilirsiniz. Özelliğin değerinin olup olmadığını denetlemek için bu işleçleri kullanabilirsiniz `Nothing`.  
  
> [!NOTE]
> Genellikle, `Is` veya `IsNot` işlecinin karşılaştırmayı gerçekleştirmek için özelliğinin değerini okuması gerekir. Ancak, özelliği şu anda depoluyorsa `Nothing`, özelliği Web hizmetinin yeni bir örneğini oluşturur ve ardından bu örneği döndürür. Ancak, Visual Basic Derleyicisi `My.WebServices` nesnenin özelliklerini özel olarak değerlendirir ve `Is` veya `IsNot` işlecinin değeri değiştirmeden özelliğin durumunu denetlemesini sağlar.  
  
## <a name="example"></a>Örnek  
 Bu örnek, `TemperatureConverter` XML `FahrenheitToCelsius` Web hizmetinin yöntemini çağırır ve sonucu döndürür.  
  
 [!code-vb[VbVbalrMyWebService#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWebService/VB/Form1.vb#1)]  
  
 Bu örneğin çalışması için, projeniz adlı `Converter`bir Web hizmetine başvurmalıdır ve Web hizmeti `ConvertTemperature` yöntemi kullanıma sunmalıdır. Daha fazla bilgi için bkz. [uygulama Web Hizmetleri 'Ne erişme](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).  
  
 Bu kod, bir Web uygulaması projesinde çalışmaz.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Web.Services.Protocols.SoapHttpClientProtocol>
- <xref:System.ArgumentException>
- [Uygulama Web Hizmetlerine Erişme](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)
