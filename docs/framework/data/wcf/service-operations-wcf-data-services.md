---
title: Hizmet işlemleri (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service operations [WCF Data Services]
- WCF Data Services, service operations
ms.assetid: 583a690a-e60f-4990-8991-d6efce069d76
ms.openlocfilehash: c5514bf32bfe03a65d7d171a500dd5d4cfde35ff
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59517414"
---
# <a name="service-operations-wcf-data-services"></a>Hizmet işlemleri (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Sunucu üzerinde yöntemleri açığa için bir veri hizmeti hizmet işlemleri tanımlamanızı sağlar. Diğer veri hizmeti kaynaklarına gibi hizmet işlemleri tarafından bir URI'leri ele alınır. Hizmet işlemleri data Service'te iş mantığı Doğrulama mantığı, rol tabanlı güvenlik uygulamak için uygulama gibi göstermek etkinleştirmeniz veya kullanıma sunmak için özellikler sorgulanırken özel. Hizmet işlemleri yöntem, türetilen veri hizmeti sınıfındaki eklenmiş olan <xref:System.Data.Services.DataService%601>. Tüm diğer veri hizmeti kaynaklarına gibi hizmet işlemi yöntemin parametre sağlayabilirsiniz. Örneğin, aşağıdaki URI işlemi hizmet (temel [hızlı](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md) veri hizmeti) değeri geçirir `London` için `city` parametresi:  
  
```  
http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'  
```  
  
 Bu hizmet işlemi tanımı aşağıdaki gibidir:  
  
 [!code-csharp[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationdef)]
 [!code-vb[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationdef)]  
  
 Kullanabileceğiniz <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> , <xref:System.Data.Services.DataService%601> doğrudan veri hizmetini kullanarak veri kaynağına erişmek için. Daha fazla bilgi için [nasıl yapılır: Hizmet işlemi tanımlama](../../../../docs/framework/data/wcf/how-to-define-a-service-operation-wcf-data-services.md).  
  
 Bir .NET Framework istemci uygulamasından bir hizmet işlemi çağırma hakkında daha fazla bilgi için bkz: [hizmet işlemleri çağırma](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md).  
  
## <a name="service-operation-requirements"></a>Hizmet işlem gereksinimleri  
 Veri hizmetine hizmet işlemlerini tanımlarken aşağıdaki gereksinimler karşılanmalıdır. Bir yöntem bu gereksinimleri karşılamıyorsa, veri hizmeti için bir hizmet işlemi olarak sunulur değil.  
  
-   İşlem, veri hizmeti sınıfındaki bir üyesi olan bir genel örnek yöntemi olmalıdır.  
  
-   İşlem yöntemi yalnızca giriş parametrelerini kabul etmesi olabilir. İleti gövdesini gönderilen veriler, veri hizmeti tarafından erişilemez.  
  
-   Parametreleri tanımlanmışsa, her parametresinin türü bir basit tür olmalıdır. İlkel olmayan türde herhangi bir veri seri hale getirilmiş ve bir dize parametresine geçirilen gerekir.  
  
-   Yöntemi, aşağıdakilerden birini döndürmesi gerekir:  
  
    -   `void` (`Nothing` Visual Basic)  
  
    -   <xref:System.Collections.Generic.IEnumerable%601>  
  
    -   <xref:System.Linq.IQueryable%601>  
  
    -   Bir varlık veri modeli verileri kullanıma sunan hizmet türü.  
  
    -   Tamsayı veya dize gibi basit bir sınıf.  
  
-   Sıralama, sayfalama ve filtreleme gibi sorgu seçenekleri desteklemek için hizmet işlemi yöntemleri döndürmelidir <xref:System.Linq.IQueryable%601>. Sorgu seçenekleri içeren hizmet işlemlerine istekleri, yalnızca iade işlemleri için reddedilir <xref:System.Collections.Generic.IEnumerable%601>.  
  
-   Gezinti Özellikleri'ni kullanarak ilgili varlıklara erişim desteklemek için hizmet işlemi döndürmelidir <xref:System.Linq.IQueryable%601>.  
  
-   Yöntem ile açıklanmamalıdır `[WebGet]` veya `[WebInvoke]` özniteliği.  
  
    -   `[WebGet]` bir GET isteği kullanılarak çağrılacak yöntem sağlar.  
  
    -   `[WebInvoke(Method = "POST")]` Bir POST isteği kullanılarak çağrılacak yöntem sağlar. Diğer <xref:System.ServiceModel.Web.WebInvokeAttribute> yöntemleri desteklenmez.  
  
-   Bir hizmet işlemi ile açıklanan <xref:System.Data.Services.SingleResultAttribute> yöntemin dönüş değeri tek bir varlık yerine varlıklar koleksiyonu olduğunu belirtir. Bu ayrım, sonuçta elde edilen serileştirme yanıt ve başka gezinme özelliği çapraz geçişleri URI'de temsil edilen şekilde belirler. Örneğin, AtomPub serileştirme kullanırken, tek bir kaynak türü örneği bir girişi öğesi ve bir örnek kümesini bir akış öğesi olarak gösterilir.  
  
## <a name="addressing-service-operations"></a>Hizmet işlemleri adresleme  
 Yöntemin adı bir URI ilk yol kesimini yerleştirerek hizmet işlemleri karşılayabilirsiniz. Örneğin, aşağıdaki URI erişen bir `GetOrdersByState` döndüren işlemi bir <xref:System.Linq.IQueryable%601> koleksiyonunu `Orders` nesneleri.  
  
```  
http://localhost:12345/Northwind.svc/GetOrdersByState?state='CA'&includeItems=true  
```  
  
 Bir hizmet işlemi çağrılırken parametreleri sorgu seçenekleri sağlanır. Önceki hizmet işlemi her iki dize parametresi kabul eden `state` ve bir Boole parametresi `includeItems` dahil etmek için ilgili olmadığını bildiren `Order_Detail` yanıt nesneleri.  
  
 Bir hizmet işlemi için geçerli dönüş türleri şunlardır:  
  
|Geçerli dönüş türleri|URI kuralları|  
|------------------------|---------------|  
|`void` (`Nothing` Visual Basic)<br /><br /> -veya-<br /><br /> Varlık türleri<br /><br /> -veya-<br /><br /> İlkel türler|Hizmet işlemi adı olan bir tek yol kesimi URI olmalıdır. Sorgu seçenekleri izin verilmez.|  
|<xref:System.Collections.Generic.IEnumerable%601>|Hizmet işlemi adı olan bir tek yol kesimi URI olmalıdır. Sonuç türü olmadığı için bir <xref:System.Linq.IQueryable%601> türü, sorgu seçenekleri izin verilmez.|  
|<xref:System.Linq.IQueryable%601>|Hizmet işlemi adını yolu yanı sıra sorgu yol kesimleri izin verilir. Sorgu seçenekleri de izin verilir.|  
  
 Hizmet işlemi dönüş türüne bağlı olarak URI'ye ek yol kesimleri veya sorgu seçenekleri eklenebilir. Örneğin, aşağıdaki URI erişen bir `GetOrdersByCity` döndüren işlemi bir <xref:System.Linq.IQueryable%601> koleksiyonunu `Orders` göre sıralanmış nesneleri `RequiredDate` yanı sıra ilgili azalan düzende `Order_Details` nesneler:  
  
```  
http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$expand=Order_Details&$orderby=RequiredDate desc  
```  
  
## <a name="service-operations-access-control"></a>Hizmet işlemleri erişim denetimi  
 Hizmet işlemleri hizmet genelinde görünürlüğü tarafından denetlenir <xref:System.Data.Services.IDataServiceConfiguration.SetServiceOperationAccessRule%2A> metodunda <xref:System.Data.Services.IDataServiceConfiguration> çok varlık görünürlüğü kümesi aynı şekilde sınıfı kullanılarak denetlenir <xref:System.Data.Services.IDataServiceConfiguration.SetEntitySetAccessRule%2A> yöntemi. Örneğin, aşağıdaki veri hizmeti tanımı'ndaki kod satırının erişime olanak tanıyan `CustomersByCity` hizmet işlemi.  
  
 [!code-csharp[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationconfig)]
 [!code-vb[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationconfig)]  
  
> [!NOTE]
>  Bir hizmet işlemi, temel alınan varlık kümesi erişimi kısıtlayarak gizli bir dönüş türü varsa, ardından hizmet işlemini istemci uygulamalar tarafından kullanılamaz.  
  
 Daha fazla bilgi için [nasıl yapılır: Hizmet işlemi tanımlama](../../../../docs/framework/data/wcf/how-to-define-a-service-operation-wcf-data-services.md).  
  
## <a name="raising-exceptions"></a>Özel durumlarını oluşturma  
 Kullanmanızı öneririz <xref:System.Data.Services.DataServiceException> bir özel durum veri hizmeti yürütmesinde yükseltmek her sınıf. Veri Hizmeti çalışma zamanı bildiğinden doğru harita HTTP yanıt iletisi için bu özel durum nesnenin özellikleri nasıl budur. Ne zaman yükseltmeniz bir <xref:System.Data.Services.DataServiceException> bir hizmet işlemi, döndürülen özel durum içinde sarmalanmış bir <xref:System.Reflection.TargetInvocationException>. Temel döndürülecek <xref:System.Data.Services.DataServiceException> kapsayan olmadan <xref:System.Reflection.TargetInvocationException>, geçersiz kılmanız gerekir <xref:System.Data.Services.DataService%601.HandleException%2A> yönteminde <xref:System.Data.Services.DataService%601>, ayıklamak <xref:System.Data.Services.DataServiceException> gelen <xref:System.Reflection.TargetInvocationException>ve aşağıdaki örnekte olduğu gibi üst düzey hata olarak döndürün:  
  
 [!code-csharp[Astoria Northwind Service#HandleExceptions](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#handleexceptions)]
 [!code-vb[Astoria Northwind Service#HandleExceptions](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#handleexceptions)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Durdurucular](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md)
