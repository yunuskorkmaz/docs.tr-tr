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
ms.openlocfilehash: 7decfdd738e71a01afa8cb32604953142b46e588
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790445"
---
# <a name="interceptors-wcf-data-services"></a>Yakalayıcılar (WCF Veri Hizmetleri)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]bir işleme özel mantık ekleyebilmeniz için, bir uygulamanın istek iletilerini ele almasını sağlar. Gelen iletilerdeki verileri doğrulamak için bu özel mantığı kullanabilirsiniz. Ayrıca, istek başına özel bir yetkilendirme ilkesi eklemek gibi bir sorgu isteğinin kapsamını kısıtlamak için de kullanabilirsiniz.  
  
 Yakatasyon, veri hizmetindeki özel olarak öznitelikli yöntemler tarafından gerçekleştirilir. Bu yöntemler tarafından [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] ileti işleme uygun noktada çağrılır. Yakalayıcılar, varlık başına ayarlanan temelinde tanımlanır ve bakım yöntemleri, hizmet işlemleri gibi istekten parametreleri kabul edemez. Bir HTTP GET isteği işlenirken çağrılan sorgu yakalayıcısı yöntemleri, bir yakacının varlık kümesi örneğinin sorgu sonuçları tarafından döndürülüp döndürülmeyeceğini belirleyen bir lambda ifadesi döndürmelidir. Bu ifade, istenen işlemi daha fazla iyileştirmek için veri hizmeti tarafından kullanılır. Aşağıda sorgu yakalayıcısı 'nın örnek bir tanımı verilmiştir.  
  
 [!code-csharp[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#queryinterceptordef)]
 [!code-vb[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#queryinterceptordef)]  
  
 Daha fazla bilgi için [nasıl yapılır: Veri hizmeti Iletilerini](how-to-intercept-data-service-messages-wcf-data-services.md)durdurur.  
  
 Sorgu olmayan işlemler işlenirken çağrılan, değişiklik dinleyicileri ( `void` `Nothing` Visual Basic) döndürmesi gerekir. Değişiklik yakalayıcısı metotları aşağıdaki iki parametreyi kabul etmelidir:  
  
1. Varlık kümesinin varlık türü ile uyumlu olan bir türün parametresi. Veri hizmeti değişiklik yakalayıcısını istediğinde, bu parametrenin değeri istek tarafından gönderilen varlık bilgilerini yansıtır.  
  
2. Türünde <xref:System.Data.Services.UpdateOperations>bir parametre. Veri hizmeti değişiklik yakalayıcısını istediğinde, bu parametrenin değeri isteğin gerçekleştirmeye çalıştığı işlemi yansıtır.  
  
 Aşağıda, değişiklik yakalayıcısı 'nın örnek bir tanımı verilmiştir.  
  
 [!code-csharp[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#changeinterceptordef)]
 [!code-vb[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#changeinterceptordef)]  
  
 Daha fazla bilgi için [nasıl yapılır: Veri hizmeti Iletilerini](how-to-intercept-data-service-messages-wcf-data-services.md)durdurur.  
  
 Aşağıdaki öznitelikler, yakalaşmayı destekler.  
  
 **[Queryyakalayıcısı (** *entitySetName* **)]**  
 <xref:System.Data.Services.QueryInterceptorAttribute> Özniteliği uygulanmış olan Yöntemler, hedeflenen varlık kümesi kaynağı için bir http get isteği alındığında çağırılır. Bu yöntemlerin, her zaman biçiminde `Expression<Func<T,bool>>`bir lambda ifadesi döndürmesi gerekir.  
  
 **[Changeyakalayıcısı (** *entitySetName* **)]**  
 Hedeflenen varlık kümesi kaynağı için http get isteği dışında bir http isteği alındığında, özniteliğiuygulanmışmetotlarçağırılır.<xref:System.Data.Services.ChangeInterceptorAttribute> Bu yöntemlerin her zaman dönmesi `void` gerekir`Nothing` (Visual Basic).  
  
 Daha fazla bilgi için [nasıl yapılır: Veri hizmeti Iletilerini](how-to-intercept-data-service-messages-wcf-data-services.md)durdurur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hizmet İşlemleri](service-operations-wcf-data-services.md)
