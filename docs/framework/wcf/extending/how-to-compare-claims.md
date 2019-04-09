---
title: 'Nasıl yapılır: Talepleri Karşılaştırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- claims [WCF], comparing
- claims [WCF]
ms.assetid: 0c4ec84d-53df-408f-8953-9bc437f56c28
ms.openlocfilehash: c6230d7618b7885d72ddfebc67157bb48ff9cb38
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122024"
---
# <a name="how-to-compare-claims"></a>Nasıl yapılır: Talepleri Karşılaştırma
Windows Communication Foundation (WCF) kimlik modeli altyapısı, yetkilendirme denetimi gerçekleştirmek için kullanılır. Bu nedenle, genel istenen eylemi gerçekleştirmek veya istenen kaynağa erişim için gerekli talep için talep yetkilendirme bağlamında karşılaştırılacak bir görevdir. Bu konu, yerleşik ve özel talep türleri dahil olmak üzere, talep Karşılaştırılacak açıklar. Kimlik modeli altyapısı hakkında daha fazla bilgi için bkz. [yönetme beyanlar ve yetkilendirmeyi kimlik modeliyle](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).  
  
 Bir talep (tür, sağa ve kaynak) eşit olup olmadığını görmek için başka bir talep aynı bölümlerinde karşı üç parçaları karşılaştırmak talep karşılaştırma gerektirir. Aşağıdaki örnekte bakın.  
  
 [!code-csharp[c_CustomClaimComparison#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#9)]
 [!code-vb[c_CustomClaimComparison#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#9)]  
  
 Her iki talepler bir talep türüne sahip <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>, sağ <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>ve bir kaynak dizesinin "kişi". Talepler, talep tüm üç bölümden eşit olarak eşit olur.  
  
 Yerleşik talep türleri kullanılarak karşılaştırılır <xref:System.IdentityModel.Claims.Claim.Equals%2A> yöntemi. Talep özgü karşılaştırma kodu gerektiğinde kullanılır. Örneğin, aşağıdaki iki kullanıcı asıl adı (UPN) talep verilen:  
  
 [!code-csharp[c_CustomClaimComparison#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#4)]
 [!code-vb[c_CustomClaimComparison#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#4)]  
  
 Karşılaştırma kodu <xref:System.IdentityModel.Claims.Claim.Equals%2A> yöntemi döndürür `true`olduğunu varsayarak `example\someone` aynı etki alanı kullanıcısı olarak tanımlayan "someone@example.com".  
  
 Özel talep türleri de karşılaştırılabilir kullanarak <xref:System.IdentityModel.Claims.Claim.Equals%2A> yöntemi. Bununla birlikte, burada tarafından döndürülen tür durumlarda <xref:System.IdentityModel.Claims.Claim.Resource%2A> talep özelliği bir temel türü dışında bir şey olduğunda <xref:System.IdentityModel.Claims.Claim.Equals%2A> döndürür `true` tarafından döndürülen değerlerin yalnızca, `Resource` özellikleri göreeşit<xref:System.IdentityModel.Claims.Claim.Equals%2A> yöntemi. Burada bu uygun olmaması durumunda, özel bir tür tarafından döndürülen `Resource` özelliği geçersiz kılmalıdır <xref:System.IdentityModel.Claims.Claim.Equals%2A> ve <xref:System.Object.GetHashCode%2A> özel işlemleri gereklidir gerçekleştirmek için yöntemleri.  
  
### <a name="comparing-built-in-claims"></a>Yerleşik talepleri karşılaştırma  
  
1.  Verilen iki örneğini <xref:System.IdentityModel.Claims.Claim> sınıfı, kullanın <xref:System.IdentityModel.Claims.Claim.Equals%2A> aşağıdaki kodda gösterildiği gibi karşılaştırma yapmak.  
  
     [!code-csharp[c_CustomClaimComparison#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#5)]
     [!code-vb[c_CustomClaimComparison#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#5)]  
  
### <a name="comparing-custom-claims-with-primitive-resource-types"></a>Özel talepler temel kaynak türleri ile karşılaştırma  
  
1.  Temel kaynak türleri ile özel talepler için karşılaştırma yerleşik talepler olduğu gibi aşağıdaki kodda gösterildiği şekilde gerçekleştirilebilir.  
  
     [!code-csharp[c_CustomClaimComparison#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#6)]
     [!code-vb[c_CustomClaimComparison#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#6)]  
  
2.  Özel talepler yapısı veya temel sınıf kaynak türleri, kaynak türü'ı geçersiz kılmalıdır için <xref:System.IdentityModel.Claims.Claim.Equals%2A> yöntemi.  
  
3.  İlk denetleyin olmadığını `obj` parametresi `null`ve bu durumda, dönüş `false`.  
  
     [!code-csharp[c_CustomClaimComparison#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#7)]
     [!code-vb[c_CustomClaimComparison#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#7)]  
  
4.  Sonraki çağrı <xref:System.Object.ReferenceEquals%2A> ve `this` ve `obj` parametre olarak. Döndürürse `true`, ardından dönüş `true`.  
  
     [!code-csharp[c_CustomClaimComparison#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#8)]
     [!code-vb[c_CustomClaimComparison#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#8)]  
  
5.  Sonraki deneme atamak `obj` sınıf türünün yerel bir değişkene. Bu başarısız olursa, başvurudur `null`. Bu gibi durumlarda, iade `false`.  
  
6.  Sağlanan talep geçerli talep doğru karşılaştırma için gereken özel bir karşılaştırma yapar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, talep kaynak ilkel olmayan türü olduğu bir özel talep karşılaştırmasını gösterir.  
  
 [!code-csharp[c_CustomClaimComparison#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#0)]
 [!code-vb[c_CustomClaimComparison#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#0)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kimlik Modeliyle Beyanlar ve Yetkilendirmeyi Yönetme](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
- [Nasıl yapılır: Özel Talep Oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-claim.md)
