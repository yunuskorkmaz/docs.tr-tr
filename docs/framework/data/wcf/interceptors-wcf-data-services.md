---
title: Dinleyiciler (WCF Veri Hizmetleri)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- query interceptors [WCF Data Services]
ms.assetid: e33ae8dc-8069-41d0-99a0-75ff28db7050
ms.openlocfilehash: f3ff08dd4cd20e7ce226750a386cfddb27731923
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="interceptors-wcf-data-services"></a>Dinleyiciler (WCF Veri Hizmetleri)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] bir uygulama için bir işlem Özel mantık ekleyebilmeleri istek iletilerini müdahale sağlar. Gelen iletilere verileri doğrulamak için bu özel mantık kullanabilirsiniz. Daha fazla kapsamı bir sorgu isteği gibi bir istek başına temelinde özel yetkilendirme ilkesi eklemek için kısıtlamak için de kullanabilirsiniz.  
  
 Kişiler tarafından ele özel öznitelikli yöntemlerinde veri hizmeti tarafından gerçekleştirilir. Bu yöntemleri tarafından çağrılır [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] ileti işleme uygun noktasında. Tek başına varlık kümesi temelinde dinleyiciler tanımlanır ve hizmet işlemleri gibi dinleyiciyi yöntemleri İstek parametreleri kabul edemez. Bir HTTP GET isteği işlerken, sorgu dinleyiciyi yöntemleri, sorgu sonuçları tarafından ayarlanan dinleyiciyi'nın varlık örneği olup olmadığını belirleyen bir lambda ifadesi döndürülmelidir döndürmesi gerekir. Bu ifade, istenen işlem daha fazla daraltmak için veri hizmeti tarafından kullanılır. Aşağıda bir örnek sorgu dinleyiciyi tanımıdır.  
  
 [!code-csharp[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#queryinterceptordef)]
 [!code-vb[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#queryinterceptordef)]  
  
 Daha fazla bilgi için bkz: [nasıl yapılır: veri hizmeti iletileri müdahale](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).  
  
 Sorgu olmayan işlemleri işlerken olarak adlandırılır, değişiklik dinleyiciler döndürmelidir `void` (`Nothing` Visual Basic'te). Değişiklik dinleyiciyi yöntemleri, aşağıdaki iki parametreyi kabul etmeniz gerekir:  
  
1.  Varlık kümesinin varlık türüyle uyumlu bir türde bir parametresi. Veri Hizmeti değişiklik dinleyiciyi çalıştırdığında, bu parametrenin değeri istek tarafından gönderilen varlık bilgileri yansıtır.  
  
2.  Türünde bir parametre <xref:System.Data.Services.UpdateOperations>. Veri Hizmeti değişiklik dinleyiciyi çalıştırdığında, bu parametrenin değeri isteği gerçekleştirmeye çalışırken işlemi yansıtır.  
  
 Aşağıda bir örnek bir değişiklik dinleyiciyi tanımıdır.  
  
 [!code-csharp[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#changeinterceptordef)]
 [!code-vb[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#changeinterceptordef)]  
  
 Daha fazla bilgi için bkz: [nasıl yapılır: veri hizmeti iletileri müdahale](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).  
  
 Aşağıdaki öznitelikler kişiler tarafından ele için desteklenir.  
  
 **[QueryInterceptor (** *EnitySetName* **)]**  
 Yöntemleriyle <xref:System.Data.Services.QueryInterceptorAttribute> uygulanan öznitelik kaynak hedef varlık kümesi için bir HTTP GET isteği alındığında çağrılır. Bu yöntemlerin her zaman biçiminde bir lambda ifadesi döndürmelidir `Expression<Func<T,bool>>`.  
  
 **[ChangeInterceptor (** *EnitySetName* **)]**  
 Yöntemleriyle <xref:System.Data.Services.ChangeInterceptorAttribute> uygulanan öznitelik kaynak hedef varlık kümesi için HTTP GET isteği dışında bir HTTP isteği alındığında çağrılır. Bu yöntemlerin her zaman döndürmelidir `void` (`Nothing` Visual Basic'te).  
  
 Daha fazla bilgi için bkz: [nasıl yapılır: veri hizmeti iletileri müdahale](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hizmet İşlemleri](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md)
