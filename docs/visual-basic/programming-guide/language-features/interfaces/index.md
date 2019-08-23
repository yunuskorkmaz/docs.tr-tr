---
title: Arabirimler (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, interfaces
- interfaces [Visual Basic], Visual Basic
- interfaces
- interfaces [Visual Basic]
ms.assetid: 61b06674-12c9-430b-be68-cc67ecee1f5b
ms.openlocfilehash: 968e5d9bb08f168e3c77b40ea42b16dc66e93e64
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956293"
---
# <a name="interfaces-visual-basic"></a>Arabirimler (Visual Basic)
*Arabirimler* , sınıfların uygulayamayacağı özellikleri, yöntemleri ve olayları tanımlar. Arabirimler, özellikleri, daha yakından ilgili özellikler, Yöntemler ve olaylar gibi küçük gruplar olarak tanımlamanızı sağlar. Bu, mevcut kodu tehlikeye atamadan arabirimlerinizde gelişmiş uygulamalar geliştirebileceğiniz için uyumluluk sorunlarını azaltır. Ek arabirimler ve uygulamalar geliştirirken dilediğiniz zaman yeni özellikler ekleyebilirsiniz.  
  
 Sınıf devralma yerine arabirimleri kullanmak isteyebileceğiniz birkaç başka neden vardır:  
  
- Arabirimler, uygulamalarınızın belirli işlevleri sağlamak için çok büyük olasılıkla ilişkisiz nesne türleri gerektirdiği durumlara daha uygundur.  
  
- Birden çok arabirim uygulayabildiğinden tek bir uygulama tanımlayabilmeniz için arabirimler temel sınıflardan daha esnektir.  
  
- Arabirimler, bir temel sınıftan uygulama devralmayı gerektirmeyen durumlarda daha iyidir.  
  
- Sınıf devralmayı kullanabilmeniz için arabirimler faydalıdır. Örneğin, yapılar sınıflardan kalýtýmla bağlanamaz, ancak arabirimleri uygulayabilirler.  
  
## <a name="declaring-interfaces"></a>Arabirimleri bildirme  
 Arabirim tanımları `Interface` ve `End Interface` deyimleri içine alınır. Deyimden sonra, bir veya daha fazla devralınmış `Inherits` arabirimi listeleyen isteğe bağlı bir ifade ekleyebilirsiniz. `Interface` Deyimler `Inherits` , açıklama haricinde bildirimde bulunan tüm diğer deyimlerden önce gelmelidir. Arabirim `Event`tanımındaki kalan deyimler `Function`, `Sub` ,,`Property`,,, ve`Enum` deyimleri olmalıdır. `Class` `Interface` `Structure` Arabirimler, `End Sub` veya `End Property`gibi uygulama kodu ile ilişkili herhangi bir uygulama kodu veya deyim içeremez.  
  
 Bir ad alanında, arabirim deyimleri `Friend` varsayılan olarak, ancak veya `Friend`olarak `Public` açıkça bildirilebilecek. Sınıflar, modüller, arabirimler ve `Public` yapılar içinde tanımlanan arabirimler varsayılan olarak,,, veya `Private` `Friend`olarak `Public` `Protected`açıkça bildirilemez.  
  
> [!NOTE]
> `Shadows` Anahtar sözcüğü tüm arabirim üyelerine uygulanabilir. Anahtar sözcüğü `Sub`, bir arabirim tanımında belirtilen `Function`, ve `Property` ifadelerine uygulanabilir. `Overloads` Ayrıca `Property` , deyimler `Default`, `ReadOnly`, veya`WriteOnly` değiştiricilere sahip olabilir. Diğer değiştiricilerin hiçbirine —`Public`, `Private`, `Friend` `Protected`,, `Shared` ,`MustOverride`,, veya`Overridable`— hiçbirine izin verilmez. `Overrides` Daha fazla bilgi için bkz. [bildirim bağlamları ve varsayılan erişim düzeyleri](../../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Örneğin, aşağıdaki kod bir arabirimi bir işlev, bir özellik ve bir olay ile tanımlar.  
  
 [!code-vb[VbVbalrOOP#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#17)]  
  
## <a name="implementing-interfaces"></a>Arabirimleri uygulama  
 Visual Basic ayrılmış sözcük `Implements` iki şekilde kullanılır. `Implements` İfade bir sınıfın veya yapının bir arabirim uyguladığını belirtir. Anahtar `Implements` sözcüğü, bir sınıf üyesi veya yapı üyesinin belirli bir arabirim üyesini uyguladığını belirtir.  
  
### <a name="implements-statement"></a>Implements Deyimi  
 Bir sınıf veya yapı bir veya daha fazla arabirim uygularsa, `Implements` `Class` veya `Structure` deyimden hemen sonra ifadesini içermesi gerekir. İfade `Implements` , bir sınıf tarafından uygulanacak arabirimlerin virgülle ayrılmış bir listesini gerektirir. Sınıf veya yapı, `Implements` anahtar sözcüğünü kullanarak tüm arabirim üyelerini uygulamalıdır.  
  
### <a name="implements-keyword"></a>Implements anahtar sözcüğü  
 Anahtar `Implements` sözcüğü, uygulanacak arabirim üyeleri için virgülle ayrılmış bir liste gerektirir. Genellikle yalnızca tek bir arabirim üyesi belirtilir, ancak birden çok üye belirtebilirsiniz. Bir arabirim üyesinin belirtimi, sınıf içindeki bir Implements ifadesinde belirtilmesi gereken arabirim adından oluşur; nokta; ve uygulanacak üye işlevin, özelliğin veya etkinliğin adı. Bir arabirim üyesini uygulayan üyenin adı herhangi bir yasal tanımlayıcıyı kullanabilir ve Visual Basic önceki sürümlerinde kullanılan `InterfaceName_MethodName` kurala sınırlı değildir.  
  
 Örneğin, aşağıdaki kod, bir arabirimin yöntemini uygulayan adlı `Sub1` bir alt yordamın nasıl bildirilemeyeceğini göstermektedir:  
  
 [!code-vb[VbVbalrOOP#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#69)]  
  
 Uygulama üyesinin parametre türleri ve dönüş türleri, arabirimdeki arabirim özelliği veya üye bildirimiyle eşleşmelidir. Bir arabirimin bir öğesini uygulamak için en yaygın yol, önceki örnekte gösterildiği gibi, arabirimiyle aynı ada sahip bir üyeye sahiptir.  
  
 `Overloads`Bir arabirim yönteminin `Overrides` `Overridable` uygulanmasınıbildirmek`Private`için,,,,,,,,,,,,,,,,,,,,,,,,,,, `Public` `Protected` `Friend`,,, ve`Static`. `Protected Friend` `MustOverride` `Default` `Shared` Öznitelik bir örnek yöntemi yerine bir sınıf tanımladığından geçerli değildir.  
  
 Kullanarak `Implements`, aşağıdaki örnekte olduğu gibi, bir arabirimde tanımlanan birden çok yöntemi uygulayan tek bir yöntem de yazabilirsiniz:  
  
 [!code-vb[VbVbalrOOP#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#70)]  
  
 Bir arabirim üyesini uygulamak için özel üye kullanabilirsiniz. Bir özel üye bir arabirimin üyesini uygularsa, bu üye, sınıfın nesne değişkenlerinde doğrudan kullanılamaz olmasına rağmen arabirim tarafından kullanılabilir hale gelir.  
  
### <a name="interface-implementation-examples"></a>Arabirim uygulama örnekleri  
 Arabirim uygulayan sınıfların tüm özelliklerini, yöntemlerini ve olaylarını uygulaması gerekir.  
  
 Aşağıdaki örnek iki arabirimi tanımlar. İkinci arabirim `Interface2`, bir ek özellik `Interface1` ve yöntemi devralır ve tanımlar.  
  
 [!code-vb[VbVbalrOOP#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#39)]  
  
 Sonraki örnek, önceki `Interface1`örnekte tanımlanan arabirimi uygular:  
  
 [!code-vb[VbVbalrOOP#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#40)]  
  
 Son örnek, öğesinden `Interface2` `Interface1`devralınan bir yöntem dahil olmak üzere şunları uygular:  
  
 [!code-vb[VbVbalrOOP#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#41)]  
  
 Salt okunur bir özelliği bir ReadWrite özelliği ile uygulayabilirsiniz (yani, uygulama sınıfında ReadOnly olarak bildirmeniz gerekmez).  Bir arabirimi uygulamak, en azından arabirimin bildirdiği üyeleri uygulamayı taahhüt eder, ancak özelliğin yazılabilir olmasını sağlamak gibi daha fazla işlevsellik sunabilirsiniz.  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[İzlenecek yol: Arabirimleri Oluşturma ve Uygulama](../../../../visual-basic/programming-guide/language-features/interfaces/walkthrough-creating-and-implementing-interfaces.md)|Kendi arabiriminizi tanımlama ve uygulama sürecinde size kılavuzluk eden ayrıntılı bir yordam sağlar.|  
|[Genel Arabirimlerde Varyans](../../concepts/covariance-contravariance/variance-in-generic-interfaces.md)|Genel arabirimlerde Kovaryans ve değişken varyansı açıklar ve .NET Framework değişken genel arabirimlerin bir listesini sağlar.|
