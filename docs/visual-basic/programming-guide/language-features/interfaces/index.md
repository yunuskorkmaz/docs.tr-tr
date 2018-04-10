---
title: Arabirimler (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, interfaces
- interfaces [Visual Basic], Visual Basic
- interfaces
- interfaces [Visual Basic]
ms.assetid: 61b06674-12c9-430b-be68-cc67ecee1f5b
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c26bb7322064d0b8cdf733e74f8b37e81b1e620c
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="interfaces-visual-basic"></a>Arabirimler (Visual Basic)
*Arabirimler* özellikleri, yöntemleri ve sınıfları uygulayabilirsiniz olayları tanımlayın. Arabirimleri, özellikleri yakından ilgili özellikleri, yöntemleri ve olayları küçük gruplar olarak tanımlamanıza olanak sağlar; Bu, var olan kodu tehlikeye atmadan arabirimlerinizi için geliştirilmiş uygulamaları geliştirebilirsiniz çünkü uyumluluk sorunları azaltır. Ek arabirimleri ve uygulamaları geliştirerek herhangi bir zamanda yeni özellikleri ekleyebilirsiniz.  
  
 Neden arabirimleri sınıf devralma yerine kullanmak isteyebilirsiniz birkaç nedeni vardır:  
  
-   Arabirimleri daha çok, büyük olasılıkla belirli işlevleri sağlamak için nesne türlerini ilgisiz, uygulamalarınızın gerektirdiği durumlar için uygundur.  
  
-   Birden çok arabirimleri uygulayabilir tek bir uygulama tanımlayabilirsiniz çünkü arabirimleri temel sınıflar daha esnektir.  
  
-   Arabirimler iyi durumda içinde uygulama bir taban sınıftan devralın gerekmez.  
  
-   Sınıf devralma kullanamadığında arabirimleri yararlı olur. Örneğin, yapıları sınıflardan devralan olamaz, ancak arabirimleri uygulayabilir.  
  
## <a name="declaring-interfaces"></a>Arabirimleri bildirme  
 Arabirim tanımları içine içinde `Interface` ve `End Interface` deyimleri. Aşağıdaki `Interface` deyimi, isteğe bağlı bir ekleyebilirsiniz `Inherits` deyimi bir veya daha fazla devralınan arabirimlerini listeler. `Inherits` Deyimleri bildiriminde açıklamaları dışındaki diğer tüm deyimleri gelmelidir. Arabirim tanımı kalan deyimlerinde olmalıdır `Event`, `Sub`, `Function`, `Property`, `Interface`, `Class`, `Structure`, ve `Enum` deyimleri. Herhangi bir uygulama kodu veya uygulama koduyla ilişkili deyimleri arabirimleri içeremez `End Sub` veya `End Property`.  
  
 Arabirim deyimleri bir ad alanında bulunan `Friend` varsayılan olarak, ancak bunlar aynı zamanda açıkça olarak bildirilebilir `Public` veya `Friend`. Arabirimleri tanımlanan sınıflar, modüller, arabirimler içinde ve yapıları olan `Public` varsayılan olarak, ancak bunlar aynı zamanda açıkça olarak bildirilebilir `Public`, `Friend`, `Protected`, veya `Private`.  
  
> [!NOTE]
>  `Shadows` Anahtar sözcüğü tüm arabirimi üyelerine uygulanabilir. `Overloads` Anahtar sözcüğü uygulanabilir `Sub`, `Function`, ve `Property` deyimleri bir arabirim tanımı'nda bildirilir. Ayrıca, `Property` deyimleri olabilir `Default`, `ReadOnly`, veya `WriteOnly` değiştiricileri. Diğer değiştiricileri hiçbiri —`Public`, `Private`, `Friend`, `Protected`, `Shared`, `Overrides`, `MustOverride`, veya `Overridable`— izin verilir. Daha fazla bilgi için bkz: [bildirim bağlamları ve varsayılan erişim düzeyleri](../../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Örneğin, aşağıdaki kod bir işlevi, bir özellik ve bir olay ile bir arabirim tanımlar.  
  
 [!code-vb[VbVbalrOOP#17](../../../../visual-basic/misc/codesnippet/VisualBasic/index_1.vb)]  
  
## <a name="implementing-interfaces"></a>Arabirimler uygulama  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Ayrılmış sözcük `Implements` iki yolla kullanılır. `Implements` Deyimi güveninin bir sınıf veya yapı bir arabirimi uygular. `Implements` Anahtar sözcüğü güveninin bir sınıf üyesi veya yapı üyesi belirli arabirim üye uygular.  
  
### <a name="implements-statement"></a>Implements Deyimi  
 Bir sınıf veya yapı bir veya daha fazla arabirimlerini uygular, içermelidir `Implements` deyimi hemen sonra `Class` veya `Structure` deyimi. `Implements` Deyim için bir sınıf tarafından uygulanacak arabirim virgülle ayrılmış bir liste gerekir. Sınıf veya yapı kullanan tüm arabirimi üyeleri uygulamalıdır `Implements` anahtar sözcüğü.  
  
### <a name="implements-keyword"></a>Implements anahtar sözcüğü  
 `Implements` Anahtar sözcüğü uygulanacak arabirim üyeleri virgülle ayrılmış bir listesini gerektirir. Genellikle, yalnızca tek bir arabirim üye belirtildi, ancak birden çok üye belirtebilirsiniz. Implements deyimi sınıfı içinde belirtilmelidir arabirim adı, arabirim üyesini belirtimi oluşur; bir süre; ve üye işlevi, özelliği veya uygulanacak olay adı. Arabirim üyesini uygulayan bir üyenin adını herhangi bir yasal tanımlayıcı kullanabilirsiniz ve bunlarla sınırlı değildir `InterfaceName_MethodName` 'ın önceki sürümlerinde kullanılan kuralı [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].  
  
 Örneğin, aşağıdaki kodu adlı bir alt yordama bildirme gösterilmektedir `Sub1` arabirim yöntemini uygular:  
  
 [!code-vb[VbVbalrOOP#69](../../../../visual-basic/misc/codesnippet/VisualBasic/index_2.vb)]  
  
 Parametre türleri ve dönüş türleri uygulayan üyesinin arabirimi arabirimi özelliği veya üye bildiriminde eşleşmelidir. Arabirim öğesi uygulamak için en yaygın arabirimi, aynı ada sahip bir üye içeren önceki örnekte gösterildiği gibi yoludur.  
  
 Bir arabirim yöntemini uyarlamasını bildirmek için de dahil olmak üzere örneği yöntemi bildirimlerinde yasal özniteliklerini kullanabilirsiniz `Overloads`, `Overrides`, `Overridable`, `Public`, `Private`, `Protected`, `Friend`, `Protected Friend`, `MustOverride`, `Default`, ve `Static`. `Shared` Özniteliği olmadığından yasal bir örnek yöntemi yerine bir sınıfı tanımlar.  
  
 Kullanarak `Implements`, birden çok yöntem aşağıdaki örnekteki gibi bir arabirim tanımlanan uygulayan tek bir yöntem de yazabilirsiniz:  
  
 [!code-vb[VbVbalrOOP#70](../../../../visual-basic/misc/codesnippet/VisualBasic/index_3.vb)]  
  
 Özel üye arabirim üyesini uygulamak için kullanabilirsiniz. Özel üye bir arabirim üye uygular, doğrudan nesne değişkenleri sınıf için kullanılabilir olmasa da bu üyede arabirimi yoluyla kullanılabilir duruma gelir.  
  
### <a name="interface-implementation-examples"></a>Arabirimi uygulama örnekleri  
 Bir arabirimi uygulayan sınıflar, tüm alt özellikleri, yöntemleri ve olayları uygulamalıdır.  
  
 Aşağıdaki örnek, iki arabirim tanımlar. İkinci arabirim `Interface2`, devralınan `Interface1` ve bir ek özellik ve yöntem tanımlar.  
  
 [!code-vb[VbVbalrOOP#39](../../../../visual-basic/misc/codesnippet/VisualBasic/index_4.vb)]  
  
 Sonraki örnek uygulayan `Interface1`, önceki örnekte tanımlanan arabirimi:  
  
 [!code-vb[VbVbalrOOP#40](../../../../visual-basic/misc/codesnippet/VisualBasic/index_5.vb)]  
  
 Son örnek uygulayan `Interface2`, bir yöntem de dahil olmak üzere devralınan `Interface1`:  
  
 [!code-vb[VbVbalrOOP#41](../../../../visual-basic/misc/codesnippet/VisualBasic/index_6.vb)]  
  
 Readonly özelliği readwrite özelliğiyle uygulayabilirsiniz (diğer bir deyişle, uygulayan sınıfa readonly bildirmeniz gerekmez).  Arabirimi uygulama en az arabirimi bildirir üyeleri uygulamak taahhüt eder, ancak özelliğinizi yazılabilir izin verme gibi daha fazla işlevsellik sunabilir.  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[İzlenecek yol: Arabirimleri oluşturma ve uygulama](../../../../visual-basic/programming-guide/language-features/interfaces/walkthrough-creating-and-implementing-interfaces.md)|Tanımlama ve kendi arabirimi uygulama işlemi boyunca sürer ayrıntılı bir yordam sağlar.|  
|[Genel arabirimlerde varyans](../../concepts/covariance-contravariance/variance-in-generic-interfaces.md)|Kovaryans ve kontravaryans genel arabirimler açıklanır ve .NET Framework değişken genel arabirimler listesini sağlar.|
