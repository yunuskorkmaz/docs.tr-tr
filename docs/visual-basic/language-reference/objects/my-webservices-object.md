---
title: My.WebServices Nesnesi
ms.date: 07/20/2015
f1_keywords:
- My.WebServices
- My.MyProject.WebServices
helpviewer_keywords:
- My.WebServices object
ms.assetid: f188dc05-2c75-41b6-bb68-122d1c3110a2
ms.openlocfilehash: 0b63b44c2cd9d55094fb83fed6c04e4de528a25c
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867201"
---
# <a name="mywebservices-object"></a>My.WebServices Nesnesi

Geçerli proje tarafından başvurulan her bir XML Web hizmetinin tek bir örneğini oluşturmaya ve bunlara erişmeye yönelik özellikler sağlar.  
  
## <a name="remarks"></a>Açıklamalar  

 `My.WebServices`Nesnesi, geçerli proje tarafından başvurulan her bir Web hizmetinin örneğini sağlar. Her örnek isteğe bağlı olarak oluşturulur. Bu Web hizmetlerine nesnenin özellikleri aracılığıyla erişebilirsiniz `My.WebServices` . Özelliğin adı, özelliğin eriştiği Web hizmetinin adıyla aynıdır. Öğesinden devralan tüm sınıflar <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> bir Web hizmetidir. Bir projeye Web Hizmetleri ekleme hakkında daha fazla bilgi için bkz. [uygulama Web Hizmetleri 'Ne erişme](../../developing-apps/programming/accessing-application-web-services.md).  
  
 `My.WebServices`Nesne yalnızca geçerli projeyle Ilişkili Web hizmetlerini kullanıma sunar. Başvurulan DLL 'lerde belirtilen Web hizmetlerine erişim sağlamaz. Bir DLL 'nin sağladığı bir Web hizmetine erişmek için, Web hizmeti 'nin adı *dlladı*biçiminde kullanmanız gerekir. *WebServiceName*. Daha fazla bilgi için bkz. [uygulama Web Hizmetleri 'Ne erişme](../../developing-apps/programming/accessing-application-web-services.md).  
  
 Nesne ve özellikleri Web uygulamaları için kullanılamaz.  
  
## <a name="properties"></a>Özellikler  

 Nesnesinin her özelliği, `My.WebServices` geçerli proje tarafından başvurulan bir Web hizmeti örneğine erişim sağlar. Özelliğin adı, özelliğin eriştiği Web hizmeti adı ile aynıdır ve özellik türü, Web hizmetinin türüyle aynıdır.  
  
> [!NOTE]
> Ad çakışması varsa, bir Web hizmetine erişmek için özellik adı *RootNamespace*_*ad*alanı \_ *HizmetAdı*olur. Örneğin, adlı iki Web hizmeti göz önünde bulundurun `Service1` . Bu hizmetlerden biri kök ad alanında ve ad alanında ise `WindowsApplication1` `Namespace1` , kullanarak bu hizmete erişirsiniz `My.WebServices.WindowsApplication1_Namespace1_Service1` .  
  
 Nesnenin özelliklerinden birine ilk kez eriştiğinizde `My.WebServices` , Web hizmetinin yeni bir örneğini oluşturur ve depolar. Bu özelliğin sonraki erişimleri, Web hizmetinin bu örneğini döndürür.  
  
 `Nothing`Bu Web hizmeti için özelliğine atayarak bir Web hizmetini atabilirsiniz. Özellik ayarlayıcısı `Nothing` saklı değere atar. Özelliği dışında bir değer atarsanız `Nothing` , ayarlayıcı bir <xref:System.ArgumentException> özel durum oluşturur.  
  
 Bir `My.WebServices` nesnenin özelliğinin, veya işlecini kullanarak bir Web hizmeti örneğini depolayıp depomadığını test edebilirsiniz `Is` `IsNot` . Özelliğin değerinin olup olmadığını denetlemek için bu işleçleri kullanabilirsiniz `Nothing` .  
  
> [!NOTE]
> Genellikle, `Is` veya `IsNot` işlecinin karşılaştırmayı gerçekleştirmek için özelliğinin değerini okuması gerekir. Ancak, özelliği şu anda depoluyorsa `Nothing` , özelliği Web hizmetinin yeni bir örneğini oluşturur ve ardından bu örneği döndürür. Ancak, Visual Basic Derleyicisi `My.WebServices` nesnenin özelliklerini özel olarak değerlendirir ve `Is` veya `IsNot` işlecinin değeri değiştirmeden özelliğin durumunu denetlemesini sağlar.  
  
## <a name="example"></a>Örnek  

 Bu örnek, `FahrenheitToCelsius` `TemperatureConverter` XML Web hizmetinin yöntemini çağırır ve sonucu döndürür.  
  
 [!code-vb[VbVbalrMyWebService#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWebService/VB/Form1.vb#1)]  
  
 Bu örneğin çalışması için, projeniz adlı bir Web hizmetine başvurmalıdır `Converter` ve Web hizmeti yöntemi kullanıma sunmalıdır `ConvertTemperature` . Daha fazla bilgi için bkz. [uygulama Web Hizmetleri 'Ne erişme](../../developing-apps/programming/accessing-application-web-services.md).  
  
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
- [Uygulama Web Hizmetlerine Erişme](../../developing-apps/programming/accessing-application-web-services.md)
