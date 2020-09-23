---
title: Arabirimler
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, interfaces
- interfaces [Visual Basic], Visual Basic
- interfaces
- interfaces [Visual Basic]
ms.assetid: 61b06674-12c9-430b-be68-cc67ecee1f5b
ms.openlocfilehash: ac5db62fec3548bfd4a99477958f4f29463267c0
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91057838"
---
# <a name="interfaces-visual-basic"></a>Arabirimler (Visual Basic)

*Arabirimler* , sınıfların uygulayamayacağı özellikleri, yöntemleri ve olayları tanımlar. Arabirimler, özellikleri, daha yakından ilgili özellikler, Yöntemler ve olaylar gibi küçük gruplar olarak tanımlamanızı sağlar. Bu, mevcut kodu tehlikeye atamadan arabirimlerinizde gelişmiş uygulamalar geliştirebileceğiniz için uyumluluk sorunlarını azaltır. Ek arabirimler ve uygulamalar geliştirirken dilediğiniz zaman yeni özellikler ekleyebilirsiniz.  
  
 Sınıf devralma yerine arabirimleri kullanmak isteyebileceğiniz birkaç başka neden vardır:  
  
- Arabirimler, uygulamalarınızın belirli işlevleri sağlamak için çok büyük olasılıkla ilişkisiz nesne türleri gerektirdiği durumlara daha uygundur.  
  
- Birden çok arabirim uygulayabildiğinden tek bir uygulama tanımlayabilmeniz için arabirimler temel sınıflardan daha esnektir.  
  
- Arabirimler, bir temel sınıftan uygulama devralmayı gerektirmeyen durumlarda daha iyidir.  
  
- Sınıf devralmayı kullanabilmeniz için arabirimler faydalıdır. Örneğin, yapılar sınıflardan kalýtýmla bağlanamaz, ancak arabirimleri uygulayabilirler.  
  
## <a name="declaring-interfaces"></a>Arabirimleri bildirme  

 Arabirim tanımları ve deyimleri içine alınır `Interface` `End Interface` . `Interface`Deyimden sonra, `Inherits` bir veya daha fazla devralınmış arabirimi listeleyen isteğe bağlı bir ifade ekleyebilirsiniz. `Inherits`Deyimler, açıklama haricinde bildirimde bulunan tüm diğer deyimlerden önce gelmelidir. Arabirim tanımındaki kalan deyimler,,,,, `Event` , `Sub` `Function` `Property` `Interface` `Class` `Structure` ve `Enum` deyimleri olmalıdır. Arabirimler, veya gibi uygulama kodu ile ilişkili herhangi bir uygulama kodu veya deyim içeremez `End Sub` `End Property` .  
  
 Bir ad alanında, arabirim deyimleri `Friend` Varsayılan olarak, ancak veya olarak açıkça bildirilebilecek `Public` `Friend` . Sınıflar, modüller, arabirimler ve yapılar içinde tanımlanan arabirimler varsayılan olarak,,, `Public` veya olarak açıkça bildirilemez `Public` `Friend` `Protected` `Private` .  
  
> [!NOTE]
> `Shadows`Anahtar sözcüğü tüm arabirim üyelerine uygulanabilir. `Overloads`Anahtar sözcüğü `Sub` , `Function` `Property` bir arabirim tanımında belirtilen, ve ifadelerine uygulanabilir. Ayrıca, `Property` deyimler `Default` ,, `ReadOnly` veya değiştiricilere sahip olabilir `WriteOnly` . Diğer değiştiricilerin hiçbirine — `Public` , `Private` ,, `Friend` , `Protected` , `Shared` `Overrides` , `MustOverride` , veya `Overridable` — hiçbirine izin verilmez. Daha fazla bilgi için bkz. [bildirim bağlamları ve varsayılan erişim düzeyleri](../../../language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Örneğin, aşağıdaki kod bir arabirimi bir işlev, bir özellik ve bir olay ile tanımlar.  
  
 [!code-vb[VbVbalrOOP#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#17)]  
  
## <a name="implementing-interfaces"></a>Arabirimleri uygulama  

 Visual Basic ayrılmış sözcük `Implements` iki şekilde kullanılır. `Implements`İfade bir sınıfın veya yapının bir arabirim uyguladığını belirtir. `Implements`Anahtar sözcüğü, bir sınıf üyesi veya yapı üyesinin belirli bir arabirim üyesini uyguladığını belirtir.  
  
### <a name="implements-statement"></a>Implements Deyimi  

 Bir sınıf veya yapı bir veya daha fazla arabirim uygularsa, `Implements` `Class` veya deyimden hemen sonra ifadesini içermesi gerekir `Structure` . `Implements`İfade, bir sınıf tarafından uygulanacak arabirimlerin virgülle ayrılmış bir listesini gerektirir. Sınıf veya yapı, anahtar sözcüğünü kullanarak tüm arabirim üyelerini uygulamalıdır `Implements` .  
  
### <a name="implements-keyword"></a>Implements anahtar sözcüğü  

 `Implements`Anahtar sözcüğü, uygulanacak arabirim üyeleri için virgülle ayrılmış bir liste gerektirir. Genellikle yalnızca tek bir arabirim üyesi belirtilir, ancak birden çok üye belirtebilirsiniz. Bir arabirim üyesinin belirtimi, sınıf içindeki bir Implements ifadesinde belirtilmesi gereken arabirim adından oluşur; nokta; ve uygulanacak üye işlevin, özelliğin veya etkinliğin adı. Bir arabirim üyesini uygulayan üyenin adı herhangi bir yasal tanımlayıcıyı kullanabilir ve `InterfaceName_MethodName` Visual Basic önceki sürümlerinde kullanılan kurala sınırlı değildir.  
  
 Örneğin, aşağıdaki kod, bir arabirimin yöntemini uygulayan adlı bir alt yordamın nasıl bildirilemeyeceğini göstermektedir `Sub1` :  
  
 [!code-vb[VbVbalrOOP#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#69)]  
  
 Uygulama üyesinin parametre türleri ve dönüş türleri, arabirimdeki arabirim özelliği veya üye bildirimiyle eşleşmelidir. Bir arabirimin bir öğesini uygulamak için en yaygın yol, önceki örnekte gösterildiği gibi, arabirimiyle aynı ada sahip bir üyeye sahiptir.  
  
 Bir arabirim yönteminin uygulamasını bildirmek için,,,,,,,,,,,,,,,,,,,,,,,,,,,,,, `Overloads` `Overrides` `Overridable` `Public` `Private` `Protected` `Friend` `Protected Friend` `MustOverride` `Default` ve `Static` gibi örnek yöntemi `Shared`Öznitelik bir örnek yöntemi yerine bir sınıf tanımladığından geçerli değildir.  
  
 Kullanarak `Implements` , aşağıdaki örnekte olduğu gibi, bir arabirimde tanımlanan birden çok yöntemi uygulayan tek bir yöntem de yazabilirsiniz:  
  
 [!code-vb[VbVbalrOOP#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#70)]  
  
 Bir arabirim üyesini uygulamak için özel üye kullanabilirsiniz. Bir özel üye bir arabirimin üyesini uygularsa, bu üye, sınıfın nesne değişkenlerinde doğrudan kullanılamaz olmasına rağmen arabirim tarafından kullanılabilir hale gelir.  
  
### <a name="interface-implementation-examples"></a>Arabirim uygulama örnekleri  

 Arabirim uygulayan sınıfların tüm özelliklerini, yöntemlerini ve olaylarını uygulaması gerekir.  
  
 Aşağıdaki örnek iki arabirimi tanımlar. İkinci arabirim, `Interface2` `Interface1` bir ek özellik ve yöntemi devralır ve tanımlar.  
  
 [!code-vb[VbVbalrOOP#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#39)]  
  
 Sonraki örnek `Interface1` , önceki örnekte tanımlanan arabirimi uygular:  
  
 [!code-vb[VbVbalrOOP#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#40)]  
  
 Son örnek `Interface2` , öğesinden devralınan bir yöntem dahil olmak üzere şunları uygular `Interface1` :  
  
 [!code-vb[VbVbalrOOP#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#41)]  
  
 Salt okunur bir özelliği bir ReadWrite özelliği ile uygulayabilirsiniz (yani, uygulama sınıfında ReadOnly olarak bildirmeniz gerekmez).  Bir arabirimi uygulamak, en azından arabirimin bildirdiği üyeleri uygulamayı taahhüt eder, ancak özelliğin yazılabilir olmasını sağlamak gibi daha fazla işlevsellik sunabilirsiniz.  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[İzlenecek yol: Arabirimleri Oluşturma ve Uygulama](walkthrough-creating-and-implementing-interfaces.md)|Kendi arabiriminizi tanımlama ve uygulama sürecinde size kılavuzluk eden ayrıntılı bir yordam sağlar.|  
|[Genel Arabirimlerde Varyans](../../concepts/covariance-contravariance/variance-in-generic-interfaces.md)|Genel arabirimlerde Kovaryans ve değişken varyansı açıklar ve .NET Framework değişken genel arabirimlerin bir listesini sağlar.|
