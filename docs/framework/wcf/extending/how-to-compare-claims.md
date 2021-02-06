---
description: 'Daha fazla bilgi edinin: nasıl yapılır: talepleri karşılaştırma'
title: 'Nasıl yapılır: Talepleri Karşılaştırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- claims [WCF], comparing
- claims [WCF]
ms.assetid: 0c4ec84d-53df-408f-8953-9bc437f56c28
ms.openlocfilehash: c2088ad3992852bdc12e7bcd71d5f3598a237b45
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99653855"
---
# <a name="how-to-compare-claims"></a>Nasıl yapılır: Talepleri Karşılaştırma

Windows Communication Foundation (WCF) içindeki kimlik modeli altyapısı, yetkilendirme denetimi gerçekleştirmek için kullanılır. Bu nedenle, ortak bir görev, yetkilendirme bağlamındaki talepleri, istenen eylemi gerçekleştirmek veya istenen kaynağa erişmek için gereken taleplerle karşılaştırmaktır. Bu konuda, yerleşik ve özel talep türleri dahil olmak üzere taleplerin nasıl karşılaştırılacağı açıklanmaktadır. Kimlik modeli altyapısı hakkında daha fazla bilgi için bkz. [kimlik modeliyle talepleri ve Yetkilendirmeyi Yönetme](../feature-details/managing-claims-and-authorization-with-the-identity-model.md).

Talep karşılaştırması, bir talebin (tür, sağ ve kaynak) üç parçasını başka bir talepteki aynı bölümlere göre karşılaştırarak eşit olup olmadığını görmenizi içerir. Aşağıdaki örneğe bakın.

[!code-csharp[c_CustomClaimComparison#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#9)]
[!code-vb[c_CustomClaimComparison#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#9)]

Her iki talep da bir talep türüne <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A> , sağına <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> ve "birisi" dizesinin bir kaynağına sahiptir. Talebin her üç bölümü de eşitse, talepler eşittir.

Yerleşik talep türleri, yöntemi kullanılarak karşılaştırılır <xref:System.IdentityModel.Claims.Claim.Equals%2A> . Gerektiğinde talebe özgü karşılaştırma kodu kullanılır. Örneğin, aşağıdaki iki Kullanıcı asıl adı (UPN) talebi verildiğinde:

[!code-csharp[c_CustomClaimComparison#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#4)]
[!code-vb[c_CustomClaimComparison#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#4)]

yöntemdeki karşılaştırma kodu, <xref:System.IdentityModel.Claims.Claim.Equals%2A> `true` `example\someone` aynı etki alanı kullanıcısını "" ile tanımlar, kabul edilir someone@example.com .

Özel talep türleri, yöntemi kullanılarak da karşılaştırılabilir <xref:System.IdentityModel.Claims.Claim.Equals%2A> . Ancak, talebin özelliği tarafından döndürülen türün <xref:System.IdentityModel.Claims.Claim.Resource%2A> ilkel bir tür dışında bir şey olduğu durumlarda, <xref:System.IdentityModel.Claims.Claim.Equals%2A> `true` yalnızca özellikler tarafından döndürülen değerler `Resource` yönteme göre eşitse döndürülür <xref:System.IdentityModel.Claims.Claim.Equals%2A> . Bunun uygun olmadığı durumlarda, özelliği tarafından döndürülen özel tür `Resource` , <xref:System.IdentityModel.Claims.Claim.Equals%2A> <xref:System.Object.GetHashCode%2A> gerekli tüm özel işlemleri gerçekleştirmek için ve yöntemlerini geçersiz kılmalıdır.

## <a name="comparing-built-in-claims"></a>Yerleşik talepler karşılaştırılıyor

1. Sınıfının iki örneği verildiğinde, <xref:System.IdentityModel.Claims.Claim> <xref:System.IdentityModel.Claims.Claim.Equals%2A> aşağıdaki kodda gösterildiği gibi, karşılaştırmayı yapmak için öğesini kullanın.

     [!code-csharp[c_CustomClaimComparison#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#5)]
     [!code-vb[c_CustomClaimComparison#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#5)]

### <a name="comparing-custom-claims-with-primitive-resource-types"></a>Özel talepleri basit kaynak türleriyle karşılaştırma

1. Temel kaynak türleriyle özel talepler için, aşağıdaki kodda gösterildiği gibi, karşılaştırma yerleşik talepler için olarak gerçekleştirilebilir.

     [!code-csharp[c_CustomClaimComparison#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#6)]
     [!code-vb[c_CustomClaimComparison#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#6)]

2. Yapı veya sınıf tabanlı kaynak türleriyle özel talepler için, kaynak türü yöntemi geçersiz kılmalıdır <xref:System.IdentityModel.Claims.Claim.Equals%2A> .

3. Önce parametrenin olup olmadığını denetleyin `obj` `null` ve varsa döndürün `false` .

     [!code-csharp[c_CustomClaimComparison#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#7)]
     [!code-vb[c_CustomClaimComparison#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#7)]

4. Sonraki çağrı <xref:System.Object.ReferenceEquals%2A> ve geçiş `this` `obj` parametreleri. Dönerse `true` geri döndürün `true` .

     [!code-csharp[c_CustomClaimComparison#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#8)]
     [!code-vb[c_CustomClaimComparison#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#8)]

5. Daha sonra `obj` sınıf türünün yerel değişkenine atamaya çalışır. Bu başarısız olursa, başvuru olur `null` . Böyle durumlarda, döndürün `false` .

6. Geçerli talebi belirtilen talebe doğru bir şekilde karşılaştırmak için gereken özel karşılaştırmayı gerçekleştirin.

## <a name="example"></a>Örnek

Aşağıdaki örnek, talep kaynağının basit olmayan bir tür olduğu özel talepler karşılaştırmasını gösterir.

[!code-csharp[c_CustomClaimComparison#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#0)]
[!code-vb[c_CustomClaimComparison#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#0)]

## <a name="see-also"></a>Ayrıca bkz.

- [Kimlik Modeliyle Beyanlar ve Yetkilendirmeyi Yönetme](../feature-details/managing-claims-and-authorization-with-the-identity-model.md)
- [Nasıl yapılır: Özel Talep Oluşturma](how-to-create-a-custom-claim.md)
