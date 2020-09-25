---
title: Yakalayıcılar (WCF Veri Hizmetleri)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- query interceptors [WCF Data Services]
ms.assetid: e33ae8dc-8069-41d0-99a0-75ff28db7050
ms.openlocfilehash: 64c5c82f33daf677e58d49655897c392f1f7b7f9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204404"
---
# <a name="interceptors-wcf-data-services"></a>Yakalayıcılar (WCF Veri Hizmetleri)

WCF Veri Hizmetleri bir uygulamaya özel mantık ekleyebilmeniz için, bir uygulamanın istek iletilerini ele almasını sağlar. Gelen iletilerdeki verileri doğrulamak için bu özel mantığı kullanabilirsiniz. Ayrıca, istek başına özel bir yetkilendirme ilkesi eklemek gibi bir sorgu isteğinin kapsamını kısıtlamak için de kullanabilirsiniz.  
  
 Yakatasyon, veri hizmetindeki özel olarak öznitelikli yöntemler tarafından gerçekleştirilir. Bu yöntemler ileti işleme uygun noktasında WCF Veri Hizmetleri tarafından çağırılır. Yakalayıcılar, varlık başına ayarlanan temelinde tanımlanır ve bakım yöntemleri, hizmet işlemleri gibi istekten parametreleri kabul edemez. Bir HTTP GET isteği işlenirken çağrılan sorgu yakalayıcısı yöntemleri, bir yakacının varlık kümesi örneğinin sorgu sonuçları tarafından döndürülüp döndürülmeyeceğini belirleyen bir lambda ifadesi döndürmelidir. Bu ifade, istenen işlemi daha fazla iyileştirmek için veri hizmeti tarafından kullanılır. Aşağıda sorgu yakalayıcısı 'nın örnek bir tanımı verilmiştir.  
  
 [!code-csharp[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#queryinterceptordef)]
 [!code-vb[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#queryinterceptordef)]  
  
 Daha fazla bilgi için bkz. [nasıl yapılır: veri hizmeti Iletilerini kesme](how-to-intercept-data-service-messages-wcf-data-services.md).  
  
 Sorgu olmayan işlemler işlenirken çağrılan, değişiklik dinleyicileri `void` ( `Nothing` Visual Basic) döndürmesi gerekir. Değişiklik yakalayıcısı metotları aşağıdaki iki parametreyi kabul etmelidir:  
  
1. Varlık kümesinin varlık türü ile uyumlu olan bir türün parametresi. Veri hizmeti değişiklik yakalayıcısını istediğinde, bu parametrenin değeri istek tarafından gönderilen varlık bilgilerini yansıtır.  
  
2. Türünde bir parametre <xref:System.Data.Services.UpdateOperations> . Veri hizmeti değişiklik yakalayıcısını istediğinde, bu parametrenin değeri isteğin gerçekleştirmeye çalıştığı işlemi yansıtır.  
  
 Aşağıda, değişiklik yakalayıcısı 'nın örnek bir tanımı verilmiştir.  
  
 [!code-csharp[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#changeinterceptordef)]
 [!code-vb[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#changeinterceptordef)]  
  
 Daha fazla bilgi için bkz. [nasıl yapılır: veri hizmeti Iletilerini kesme](how-to-intercept-data-service-messages-wcf-data-services.md).  
  
 Aşağıdaki öznitelikler, yakalaşmayı destekler.  
  
 **[Queryyakalayıcısı (** *entitySetName* **)]**  
 Özniteliği uygulanmış olan Yöntemler, <xref:System.Data.Services.QueryInterceptorAttribute> hedeflenen varlık kümesi kaynağı için BIR http get isteği alındığında çağırılır. Bu yöntemlerin, her zaman biçiminde bir lambda ifadesi döndürmesi gerekir `Expression<Func<T,bool>>` .  
  
 **[Changeyakalayıcısı (** *entitySetName* **)]**  
 <xref:System.Data.Services.ChangeInterceptorAttribute>Hedeflenen varlık kümesi kaynağı IÇIN http get isteği dışında BIR http isteği alındığında, özniteliği uygulanmış metotlar çağırılır. Bu yöntemlerin her zaman dönmesi gerekir `void` ( `Nothing` Visual Basic).  
  
 Daha fazla bilgi için bkz. [nasıl yapılır: veri hizmeti Iletilerini kesme](how-to-intercept-data-service-messages-wcf-data-services.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hizmet İşlemleri](service-operations-wcf-data-services.md)
