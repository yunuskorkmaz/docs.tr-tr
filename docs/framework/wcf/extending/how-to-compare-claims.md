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
ms.openlocfilehash: e2d3d33900dd894eea77420aac444ebde0df9a43
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68970773"
---
# <a name="how-to-compare-claims"></a>Nasıl yapılır: Talepleri Karşılaştırma

Windows Communication Foundation (WCF) içindeki kimlik modeli altyapısı, yetkilendirme denetimi gerçekleştirmek için kullanılır. Bu nedenle, ortak bir görev, yetkilendirme bağlamındaki talepleri, istenen eylemi gerçekleştirmek veya istenen kaynağa erişmek için gereken taleplerle karşılaştırmaktır. Bu konuda, yerleşik ve özel talep türleri dahil olmak üzere taleplerin nasıl karşılaştırılacağı açıklanmaktadır. Kimlik modeli altyapısı hakkında daha fazla bilgi için bkz. [kimlik modeliyle talepleri ve Yetkilendirmeyi Yönetme](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).

Talep karşılaştırması, bir talebin (tür, sağ ve kaynak) üç parçasını başka bir talepteki aynı bölümlere göre karşılaştırarak eşit olup olmadığını görmenizi içerir. Aşağıdaki örnekte bakın.

[!code-csharp[c_CustomClaimComparison#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#9)]
[!code-vb[c_CustomClaimComparison#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#9)]

Her iki talep da bir talep türüne <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>, <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>sağına ve "birisi" dizesinin bir kaynağına sahiptir. Talebin her üç bölümü de eşitse, talepler eşittir.

Yerleşik talep türleri, <xref:System.IdentityModel.Claims.Claim.Equals%2A> yöntemi kullanılarak karşılaştırılır. Gerektiğinde talebe özgü karşılaştırma kodu kullanılır. Örneğin, aşağıdaki iki Kullanıcı asıl adı (UPN) talebi verildiğinde:

[!code-csharp[c_CustomClaimComparison#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#4)]
[!code-vb[c_CustomClaimComparison#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#4)]

<xref:System.IdentityModel.Claims.Claim.Equals%2A> `example\someone` yöntemdeki karşılaştırma kodu, aynı etki alanı kullanıcısını "someone@example.com" ile tanımlar ,kabuledilir.`true`

Özel talep türleri, <xref:System.IdentityModel.Claims.Claim.Equals%2A> yöntemi kullanılarak da karşılaştırılabilir. Ancak, talebin <xref:System.IdentityModel.Claims.Claim.Resource%2A> özelliği tarafından döndürülen türün ilkel bir tür <xref:System.IdentityModel.Claims.Claim.Equals%2A> dışında bir şey olduğu durumlarda, yalnızca `Resource` Özellikler tarafından döndürülen değerler şuna göre `true` eşitse,döndürür.<xref:System.IdentityModel.Claims.Claim.Equals%2A> yöntemi. Bunun uygun olmadığı durumlarda, `Resource` özelliği tarafından döndürülen özel tür, <xref:System.IdentityModel.Claims.Claim.Equals%2A> gerekli tüm özel işlemleri gerçekleştirmek için ve <xref:System.Object.GetHashCode%2A> yöntemlerini geçersiz kılmalıdır.

## <a name="comparing-built-in-claims"></a>Yerleşik talepler karşılaştırılıyor

1. <xref:System.IdentityModel.Claims.Claim> Sınıfının iki örneği verildiğinde, aşağıdaki kodda gösterildiği gibi <xref:System.IdentityModel.Claims.Claim.Equals%2A> , karşılaştırmayı yapmak için öğesini kullanın.

     [!code-csharp[c_CustomClaimComparison#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#5)]
     [!code-vb[c_CustomClaimComparison#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#5)]

### <a name="comparing-custom-claims-with-primitive-resource-types"></a>Özel talepleri basit kaynak türleriyle karşılaştırma

1. Temel kaynak türleriyle özel talepler için, aşağıdaki kodda gösterildiği gibi, karşılaştırma yerleşik talepler için olarak gerçekleştirilebilir.

     [!code-csharp[c_CustomClaimComparison#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#6)]
     [!code-vb[c_CustomClaimComparison#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#6)]

2. Yapı veya sınıf tabanlı kaynak türleriyle özel talepler için, kaynak türü <xref:System.IdentityModel.Claims.Claim.Equals%2A> yöntemi geçersiz kılmalıdır.

3. Önce `obj` `false`parametrenin olupolmadığınıdenetleyinvevarsadöndürün.`null`

     [!code-csharp[c_CustomClaimComparison#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#7)]
     [!code-vb[c_CustomClaimComparison#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#7)]

4. Sonraki çağrı <xref:System.Object.ReferenceEquals%2A> `this` ve`obj` geçiş parametreleri. Dönerse `true`geri döndürün `true`.

     [!code-csharp[c_CustomClaimComparison#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#8)]
     [!code-vb[c_CustomClaimComparison#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#8)]

5. Daha sonra sınıf türünün `obj` yerel değişkenine atamaya çalışır. Bu başarısız olursa, başvuru olur `null`. Böyle durumlarda, döndürün `false`.

6. Geçerli talebi belirtilen talebe doğru bir şekilde karşılaştırmak için gereken özel karşılaştırmayı gerçekleştirin.

## <a name="example"></a>Örnek

Aşağıdaki örnek, talep kaynağının basit olmayan bir tür olduğu özel talepler karşılaştırmasını gösterir.

[!code-csharp[c_CustomClaimComparison#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#0)]
[!code-vb[c_CustomClaimComparison#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#0)]

## <a name="see-also"></a>Ayrıca bkz.

- [Kimlik Modeliyle Talep ve Yetkilendirmeyi Yönetme](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
- [Nasıl yapılır: Özel talep oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-claim.md)
