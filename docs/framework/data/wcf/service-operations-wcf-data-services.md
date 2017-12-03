---
title: "Hizmet işlemleri (WCF Veri Hizmetleri)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service operations [WCF Data Services]
- WCF Data Services, service operations
ms.assetid: 583a690a-e60f-4990-8991-d6efce069d76
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 578f62773fc63ac48977116834bb5cd3238050d3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="service-operations-wcf-data-services"></a>Hizmet işlemleri (WCF Veri Hizmetleri)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]Sunucu üzerindeki yöntemleri kullanıma sunmak için veri hizmeti hizmet işlemleri tanımlamanızı sağlar. Veri Hizmeti kaynaklar gibi hizmet işlemleri URI tarafından ele alınmıştır. Hizmet işlemleri, bir veri hizmeti iş mantığı gibi rol tabanlı güvenlik, uygulamak için doğrulama mantığını uygulamak için kullanıma sunmak etkinleştirin veya özellikleri sorgulama kullanıma sunmak için özelleştirilmiş. Hizmet işlemleri yöntemlerdir türetilen veri hizmet sınıfı eklenen <xref:System.Data.Services.DataService%601>. Tüm veri hizmeti kaynaklar gibi hizmet işlemi yöntemi için parametreler sağlayabilir. Örneğin, aşağıdaki işlemi URI hizmet (temel [Hızlı Başlangıç](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md) veri hizmeti) değeri geçirir `London` için `city` parametre:  
  
```  
http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'  
```  
  
 Bu hizmet işlemi tanımı aşağıdaki gibidir:  
  
 [!code-csharp[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#serviceoperationdef)]
 [!code-vb[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#serviceoperationdef)]  
  
 Kullanabileceğiniz <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> , <xref:System.Data.Services.DataService%601> doğrudan veri hizmeti kullanarak veri kaynağına erişmek için. Daha fazla bilgi için bkz: [nasıl yapılır: bir hizmet işlemi tanımlamak](../../../../docs/framework/data/wcf/how-to-define-a-service-operation-wcf-data-services.md).  
  
 Bir .NET Framework istemci uygulamasından bir hizmet işlemi çağırma hakkında daha fazla bilgi için bkz: [hizmet işlemlerini çağırma](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md).  
  
## <a name="service-operation-requirements"></a>Hizmet işlem gereksinimleri  
 Veri Hizmeti hizmet işlemleri tanımlarken, aşağıdaki gereksinimleri geçerlidir. Bir yöntem bu gereksinimlerini karşılamıyorsa, veri hizmeti için bir hizmet işlemi olarak sunulur değil.  
  
-   İşlemi, veri hizmeti sınıf üyesi olan bir ortak örnek yöntemi olması gerekir.  
  
-   İşlem yöntemi yalnızca giriş parametreleri kabul edebilir. İleti gövdesinde gönderilen veriler veri hizmeti tarafından erişilemiyor.  
  
-   Parametreleri tanımlanmışsa, her parametrenin türü basit tür olmalıdır. Bir basit olmayan türde herhangi bir veri seri hale getirilmiş ve bir dize parametresi geçirildi.  
  
-   Yöntem aşağıdakilerden birini döndürmesi gerekir:  
  
    -   `void`(`Nothing` Visual Basic)  
  
    -   <xref:System.Collections.Generic.IEnumerable%601>  
  
    -   <xref:System.Linq.IQueryable%601>  
  
    -   Bir varlık türü veri modelinde verileri düzenlemenizi sağlayan hizmet.  
  
    -   Tamsayı veya dize gibi basit bir sınıf.  
  
-   Sıralama, disk belleği ve filtreleme gibi sorgu seçeneklerini desteklemek için hizmet işlemi yöntemleri döndürmelidir <xref:System.Linq.IQueryable%601>. Sorgu seçenekleri hizmet işlemleri istekleri, yalnızca geri işlemleri için reddedilir <xref:System.Collections.Generic.IEnumerable%601>.  
  
-   İlgili varlık Gezinti özellikleri kullanarak erişim desteklemek için hizmet işlemi döndürmelidir <xref:System.Linq.IQueryable%601>.  
  
-   Yöntem ile Açıklama eklenmelidir `[WebGet]` veya `[WebInvoke]` özniteliği.  
  
    -   `[WebGet]`GET isteği kullanarak çağrılacak yöntem sağlar.  
  
    -   `[WebInvoke(Method = "POST")]`Bir POST isteği kullanarak çağrılacak yöntem sağlar. Diğer <xref:System.ServiceModel.Web.WebInvokeAttribute> yöntemleri desteklenmiyor.  
  
-   Bir hizmet işlemi ile Açıklama <xref:System.Data.Services.SingleResultAttribute> yöntemden dönüş değeri bir varlıklar koleksiyonu yerine tek bir varlık olduğunu belirtir. Bu ayrım yanıt ve ek gezinti özelliği çapraz geçişlerine URI'de temsil edilir şekilde elde edilen serileştirmek belirler. Örneğin, AtomPub serileştirme kullanırken, tek bir kaynak türü örneği olarak bir giriş öğesini ve bir örnek kümesini akış öğesi olarak temsil edilir.  
  
## <a name="addressing-service-operations"></a>Hizmet işlemleri adresleme  
 Bir URI ilk yol kesimi yöntemin adını koyarak hizmet işlemleri karşılayabilir. Örnek olarak, aşağıdaki URI erişen bir `GetOrdersByState` döndüren işlemi bir <xref:System.Linq.IQueryable%601> koleksiyonu `Orders` nesneleri.  
  
```  
http://localhost:12345/Northwind.svc/GetOrdersByState?state='CA'&includeItems=true  
```  
  
 Bir hizmet işlemi çağırırken parametre olarak sorgu seçenekleri sağlanır. Önceki hizmet işlemi her iki dize parametresi kabul `state` ve bir Boolean parametresiyle `includeItems` belirten dahil etmek için ilgili olmadığını `Order_Detail` yanıt nesneleri.  
  
 Bir hizmet işlemi için geçerli dönüş türleri şunlardır:  
  
|Geçerli dönüş türleri|URI kuralları|  
|------------------------|---------------|  
|`void`(`Nothing` Visual Basic)<br /><br /> veya<br /><br /> Varlık türleri<br /><br /> veya<br /><br /> İlkel türler|Hizmet işlemini adı tek bir yol kesimi URI olmalıdır. Sorgu seçeneklerine izin verilmiyor.|  
|<xref:System.Collections.Generic.IEnumerable%601>|Hizmet işlemini adı tek bir yol kesimi URI olmalıdır. Sonuç türü olmadığından bir <xref:System.Linq.IQueryable%601> türü, sorgu seçeneklerine izin verilmez.|  
|<xref:System.Linq.IQueryable%601>|Sorgu yol kesimleri hizmet işlemi adını yolu ek olarak izin verilir. Sorgu seçenekleri de izin verilir.|  
  
 Ek yol kesimleri veya sorgu seçeneklerini URI hizmet işlemi dönüş türüne bağlı olarak eklenebilir. Örneğin, aşağıdaki URI erişen bir `GetOrdersByCity` döndüren işlemi bir <xref:System.Linq.IQueryable%601> koleksiyonu `Orders` göre sıralanmış nesneleri `RequiredDate` ilgili birlikte azalan `Order_Details` nesneler:  
  
```  
http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$expand=Order_Details&$orderby=RequiredDate desc  
```  
  
## <a name="service-operations-access-control"></a>Hizmet işlemleri erişim denetimi  
 Hizmet geneli görünürlüğünü hizmet işlemleri tarafından denetlenir <xref:System.Data.Services.IDataServiceConfiguration.SetServiceOperationAccessRule%2A> yöntemi <xref:System.Data.Services.IDataServiceConfiguration> varlık görünürlüğü kümesi benzer şekilde sınıfında kullanılarak denetlenir <xref:System.Data.Services.IDataServiceConfiguration.SetEntitySetAccessRule%2A> yöntemi. Örneğin, veri hizmeti tanımı kod aşağıdaki satırı erişimini etkinleştirir `CustomersByCity` hizmet işlemi.  
  
 [!code-csharp[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#serviceoperationconfig)]
 [!code-vb[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#serviceoperationconfig)]  
  
> [!NOTE]
>  Bir hizmet işlemi temel varlık kümeleri erişimi kısıtlayarak gizli bir dönüş türü varsa, hizmet işlemini istemci uygulamaları için kullanılabilir olmaz.  
  
 Daha fazla bilgi için bkz: [nasıl yapılır: bir hizmet işlemi tanımlamak](../../../../docs/framework/data/wcf/how-to-define-a-service-operation-wcf-data-services.md).  
  
## <a name="raising-exceptions"></a>Özel durumlarını oluşturma  
 Kullanmanızı öneririz <xref:System.Data.Services.DataServiceException> bir özel durum veri hizmeti yürütmesinde Yükselt her sınıf. Veri Hizmeti çalışma zamanı bildiği için bu özel durum nesnesi özelliklerini doğru HTTP yanıt iletisi eşleme budur. Yükselttiğinizde bir <xref:System.Data.Services.DataServiceException> döndürülen özel durum bir hizmet işlemi sarmalanmış bir <xref:System.Reflection.TargetInvocationException>. Temel döndürülecek <xref:System.Data.Services.DataServiceException> kapsayan olmadan <xref:System.Reflection.TargetInvocationException>, geçersiz kılmanız gerekir <xref:System.Data.Services.DataService%601.HandleException%2A> yönteminde <xref:System.Data.Services.DataService%601>, ayıklamak <xref:System.Data.Services.DataServiceException> gelen <xref:System.Reflection.TargetInvocationException>ve aşağıdaki örnekteki gibi üst düzey hata olarak döndürün:  
  
 [!code-csharp[Astoria Northwind Service#HandleExceptions](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#handleexceptions)]
 [!code-vb[Astoria Northwind Service#HandleExceptions](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#handleexceptions)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Dinleyiciler](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md)
