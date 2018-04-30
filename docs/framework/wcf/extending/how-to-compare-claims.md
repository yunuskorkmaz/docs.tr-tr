---
title: 'Nasıl yapılır: Beyanları Karşılaştırma'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- claims [WCF], comparing
- claims [WCF]
ms.assetid: 0c4ec84d-53df-408f-8953-9bc437f56c28
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5188ed17e3a10bfd93b885fcdd93e01391dd8256
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-compare-claims"></a>Nasıl yapılır: Beyanları Karşılaştırma
Kimlik modeli altyapısında [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] yetkilendirme denetimi gerçekleştirmek için kullanılır. Bu nedenle, bir ortak istenen eylemi gerçekleştirmek ya da istenen kaynağa erişmek için gerekli talep için talep yetkilendirme bağlamında karşılaştırmak için bir görevdir. Bu konu, yerleşik ve özel talep türleri dahil olmak üzere, talep Karşılaştırılacak açıklar. Kimlik modeli altyapısı hakkında daha fazla bilgi için bkz: [yönetme beyanlar ve yetkilendirmeyi kimlik modeliyle](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).  
  
 Talep karşılaştırma eşit olup olmadığını görmek için başka bir talep aynı bölümlerinde karşı talep (türü, sağa ve kaynak) üç bölümden karşılaştırma içerir. Aşağıdaki örnekte bakın.  
  
 [!code-csharp[c_CustomClaimComparison#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#9)]
 [!code-vb[c_CustomClaimComparison#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#9)]  
  
 Her iki talep bir talep türüne sahip <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>, sağ <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>ve kaynak dizesi "biri". Talep tüm üç bölümden eşit olduğu gibi kendilerini eşit taleplerdir.  
  
 Yerleşik talep türlerini kullanarak karşılaştırılır <xref:System.IdentityModel.Claims.Claim.Equals%2A> yöntemi. Talep özgü karşılaştırma kod gerektiğinde kullanılır. Örneğin, aşağıdaki iki kullanıcı asıl adı (UPN) talep verilen:  
  
 [!code-csharp[c_CustomClaimComparison#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#4)]
 [!code-vb[c_CustomClaimComparison#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#4)]  
  
 Karşılaştırma kodda <xref:System.IdentityModel.Claims.Claim.Equals%2A> yöntemi döndürür `true`olduğunu varsayarak `example\someone` aynı etki alanı kullanıcısı olarak tanımlayan "someone@example.com".  
  
 Özel talep türleri de karşılaştırılabilir kullanarak <xref:System.IdentityModel.Claims.Claim.Equals%2A> yöntemi. Ancak, burada türü tarafından döndürülen durumlarda <xref:System.IdentityModel.Claims.Claim.Resource%2A> talep özelliği bir ilkel türe dışında bir şey olduğunda <xref:System.IdentityModel.Claims.Claim.Equals%2A> döndürür `true` tarafından döndürülen değerlerin yalnızca varsa `Resource` özellikleri göre eşit<xref:System.IdentityModel.Claims.Claim.Equals%2A> yöntemi. Bu olduğu uygun durumlarda, özel türü tarafından döndürülen `Resource` özelliği geçersiz <xref:System.IdentityModel.Claims.Claim.Equals%2A> ve <xref:System.Object.GetHashCode%2A> ne olursa olsun özel işleme gereklidir gerçekleştirmek için yöntemleri.  
  
### <a name="comparing-built-in-claims"></a>Yerleşik talep karşılaştırma  
  
1.  İki örneği verilen <xref:System.IdentityModel.Claims.Claim> sınıfı, kullanın <xref:System.IdentityModel.Claims.Claim.Equals%2A> aşağıdaki kodda gösterildiği gibi karşılaştırma yapmak için.  
  
     [!code-csharp[c_CustomClaimComparison#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#5)]
     [!code-vb[c_CustomClaimComparison#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#5)]  
  
### <a name="comparing-custom-claims-with-primitive-resource-types"></a>Özel talep ilkel kaynak türleri ile karşılaştırma  
  
1.  İlkel kaynak türleri ile özel talepler için karşılaştırma yerleşik talepler için olduğu gibi aşağıdaki kodda gösterildiği gibi gerçekleştirilebilir.  
  
     [!code-csharp[c_CustomClaimComparison#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#6)]
     [!code-vb[c_CustomClaimComparison#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#6)]  
  
2.  Özel talep yapısı veya temel sınıfı kaynak türleri, kaynak türü geçersiz kılmalıdır için <xref:System.IdentityModel.Claims.Claim.Equals%2A> yöntemi.  
  
3.  İlk denetleyin olup olmadığını `obj` parametresi `null`ve bulunursa, `false`.  
  
     [!code-csharp[c_CustomClaimComparison#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#7)]
     [!code-vb[c_CustomClaimComparison#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#7)]  
  
4.  Sonraki çağrı <xref:System.Object.ReferenceEquals%2A> ve geçirin `this` ve `obj` parametre olarak. Döndürürse `true`, ardından dönüş `true`.  
  
     [!code-csharp[c_CustomClaimComparison#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#8)]
     [!code-vb[c_CustomClaimComparison#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#8)]  
  
5.  Sonraki denemesi atamak `obj` yerel değişkene sınıf türü. Bu başarısız olursa, başvurudur `null`. Böyle durumlarda, dönüş `false`.  
  
6.  Özel karşılaştırma doğru geçerli talep kümesine sağlanan talep karşılaştırmak gerekli gerçekleştirin.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, talep kaynak olmayan ilkel türünün olduğu özel talep karşılaştırması gösterir.  
  
 [!code-csharp[c_CustomClaimComparison#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#0)]
 [!code-vb[c_CustomClaimComparison#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#0)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kimlik Modeliyle Talep ve Yetkilendirmeyi Yönetme](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 [Nasıl yapılır: Özel Talep Oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-claim.md)
