---
title: Arabirimler
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, interfaces
- interfaces [Visual Basic], Visual Basic
- interfaces
- interfaces [Visual Basic]
ms.assetid: 61b06674-12c9-430b-be68-cc67ecee1f5b
ms.openlocfilehash: 619aa6695db756e56a836fd76693cc8a3976f8e2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345050"
---
# <a name="interfaces-visual-basic"></a>Arabirimler (Visual Basic)
*Arabirimler* , sınıfların uygulayamayacağı özellikleri, yöntemleri ve olayları tanımlar. Arabirimler, özellikleri, daha yakından ilgili özellikler, Yöntemler ve olaylar gibi küçük gruplar olarak tanımlamanızı sağlar. Bu, mevcut kodu tehlikeye atamadan arabirimlerinizde gelişmiş uygulamalar geliştirebileceğiniz için uyumluluk sorunlarını azaltır. Ek arabirimler ve uygulamalar geliştirirken dilediğiniz zaman yeni özellikler ekleyebilirsiniz.  
  
 Sınıf devralma yerine arabirimleri kullanmak isteyebileceğiniz birkaç başka neden vardır:  
  
- Arabirimler, uygulamalarınızın belirli işlevleri sağlamak için çok büyük olasılıkla ilişkisiz nesne türleri gerektirdiği durumlara daha uygundur.  
  
- Birden çok arabirim uygulayabildiğinden tek bir uygulama tanımlayabilmeniz için arabirimler temel sınıflardan daha esnektir.  
  
- Arabirimler, bir temel sınıftan uygulama devralmayı gerektirmeyen durumlarda daha iyidir.  
  
- Sınıf devralmayı kullanabilmeniz için arabirimler faydalıdır. Örneğin, yapılar sınıflardan kalýtýmla bağlanamaz, ancak arabirimleri uygulayabilirler.  
  
## <a name="declaring-interfaces"></a>Arabirimleri bildirme  
 Arabirim tanımları `Interface` ve `End Interface` deyimlerinin içine alınır. `Interface` deyimden sonra, bir veya daha fazla devralınmış arabirimi listeleyen isteğe bağlı bir `Inherits` açıklaması ekleyebilirsiniz. `Inherits` deyimleri, açıklama haricinde Bildirimdeki tüm diğer deyimlerden önce gelmelidir. Arabirim tanımındaki kalan deyimler `Event`, `Sub`, `Function`, `Property`, `Interface`, `Class`, `Structure`ve `Enum` deyimleri olmalıdır. Arabirimler, `End Sub` veya `End Property`gibi uygulama kodu ile ilişkili herhangi bir uygulama kodu veya deyim içeremez.  
  
 Bir ad alanında, arabirim deyimleri varsayılan olarak `Friend`, ancak aynı zamanda `Public` veya `Friend`olarak açıkça bildirilebilecek. Sınıflar, modüller, arabirimler ve yapılar içinde tanımlanan arabirimler, varsayılan olarak `Public`, ancak `Public`, `Friend`, `Protected`veya `Private`olarak açıkça de tanımlanabilir.  
  
> [!NOTE]
> `Shadows` anahtar sözcüğü tüm arabirim üyelerine uygulanabilir. `Overloads` anahtar sözcüğü, bir arabirim tanımında belirtilen `Sub`, `Function`ve `Property` deyimlerine uygulanabilir. Ayrıca, `Property` deyimlerde `Default`, `ReadOnly`veya `WriteOnly` değiştiricileri bulunabilir. Diğer değiştiricilerin hiçbirine —`Public`, `Private`, `Friend`, `Protected`, `Shared`, `Overrides`, `MustOverride`veya `Overridable`izin verilir. Daha fazla bilgi için bkz. [bildirim bağlamları ve varsayılan erişim düzeyleri](../../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Örneğin, aşağıdaki kod bir arabirimi bir işlev, bir özellik ve bir olay ile tanımlar.  
  
 [!code-vb[VbVbalrOOP#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#17)]  
  
## <a name="implementing-interfaces"></a>Arabirimleri uygulama  
 Visual Basic ayrılmış sözcük `Implements` iki şekilde kullanılır. `Implements` ifade bir sınıfın veya yapının bir arabirim uyguladığını belirtir. `Implements` anahtar sözcüğü, bir sınıf üyesi veya yapı üyesinin belirli bir arabirim üyesini uyguladığını belirtir.  
  
### <a name="implements-statement"></a>Implements Deyimi  
 Bir sınıf veya yapı bir veya daha fazla arabirim uygularsa, `Class` veya `Structure` deyimden hemen sonra `Implements` ifadesini içermesi gerekir. `Implements` ifade, bir sınıf tarafından uygulanacak arabirimlerin virgülle ayrılmış bir listesini gerektirir. Sınıf veya yapı, `Implements` anahtar sözcüğünü kullanarak tüm arabirim üyelerini uygulamalıdır.  
  
### <a name="implements-keyword"></a>Implements anahtar sözcüğü  
 `Implements` anahtar sözcüğü, uygulanacak arabirim üyeleri için virgülle ayrılmış bir liste gerektirir. Genellikle yalnızca tek bir arabirim üyesi belirtilir, ancak birden çok üye belirtebilirsiniz. Bir arabirim üyesinin belirtimi, sınıf içindeki bir Implements ifadesinde belirtilmesi gereken arabirim adından oluşur; nokta; ve uygulanacak üye işlevin, özelliğin veya etkinliğin adı. Bir arabirim üyesini uygulayan üyenin adı herhangi bir yasal tanımlayıcıyı kullanabilir ve Visual Basic önceki sürümlerinde kullanılan `InterfaceName_MethodName` kuralıyla sınırlı değildir.  
  
 Örneğin, aşağıdaki kod, bir arabirimin yöntemini uygulayan `Sub1` adlı bir alt yordamın nasıl bildirilemeyeceğini göstermektedir:  
  
 [!code-vb[VbVbalrOOP#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#69)]  
  
 Uygulama üyesinin parametre türleri ve dönüş türleri, arabirimdeki arabirim özelliği veya üye bildirimiyle eşleşmelidir. Bir arabirimin bir öğesini uygulamak için en yaygın yol, önceki örnekte gösterildiği gibi, arabirimiyle aynı ada sahip bir üyeye sahiptir.  
  
 Bir arabirim yönteminin uygulamasını bildirmek için `Overloads`, `Overrides`, `Overridable`, `Public`, `Private`, `Protected`, `Friend`, `Protected Friend`, `MustOverride`, `Default`ve `Static`dahil olmak üzere örnek yöntem bildirimlerinde geçerli olan öznitelikleri kullanabilirsiniz. Örnek yöntemi yerine bir sınıf tanımladığından `Shared` özniteliği geçerli değil.  
  
 `Implements`kullanarak, aşağıdaki örnekte olduğu gibi, bir arabirimde tanımlanan birden çok yöntemi uygulayan tek bir yöntem de yazabilirsiniz:  
  
 [!code-vb[VbVbalrOOP#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#70)]  
  
 Bir arabirim üyesini uygulamak için özel üye kullanabilirsiniz. Bir özel üye bir arabirimin üyesini uygularsa, bu üye, sınıfın nesne değişkenlerinde doğrudan kullanılamaz olmasına rağmen arabirim tarafından kullanılabilir hale gelir.  
  
### <a name="interface-implementation-examples"></a>Arabirim uygulama örnekleri  
 Arabirim uygulayan sınıfların tüm özelliklerini, yöntemlerini ve olaylarını uygulaması gerekir.  
  
 Aşağıdaki örnek iki arabirimi tanımlar. İkinci arabirim `Interface2`, `Interface1` devralır ve ek bir özellik ve yöntemi tanımlar.  
  
 [!code-vb[VbVbalrOOP#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#39)]  
  
 Sonraki örnek, önceki örnekte tanımlanan arabirimi `Interface1`uygular:  
  
 [!code-vb[VbVbalrOOP#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#40)]  
  
 Son örnek, `Interface1`devralınmış bir yöntem dahil `Interface2`uygular:  
  
 [!code-vb[VbVbalrOOP#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#41)]  
  
 Salt okunur bir özelliği bir ReadWrite özelliği ile uygulayabilirsiniz (yani, uygulama sınıfında ReadOnly olarak bildirmeniz gerekmez).  Bir arabirimi uygulamak, en azından arabirimin bildirdiği üyeleri uygulamayı taahhüt eder, ancak özelliğin yazılabilir olmasını sağlamak gibi daha fazla işlevsellik sunabilirsiniz.  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[İzlenecek yol: Arabirimleri Oluşturma ve Uygulama](../../../../visual-basic/programming-guide/language-features/interfaces/walkthrough-creating-and-implementing-interfaces.md)|Kendi arabiriminizi tanımlama ve uygulama sürecinde size kılavuzluk eden ayrıntılı bir yordam sağlar.|  
|[Genel Arabirimlerde Varyans](../../concepts/covariance-contravariance/variance-in-generic-interfaces.md)|Genel arabirimlerde Kovaryans ve değişken varyansı açıklar ve .NET Framework değişken genel arabirimlerin bir listesini sağlar.|
