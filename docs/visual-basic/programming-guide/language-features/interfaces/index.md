---
title: Arabirimler (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
  - 'Visual Basic code, interfaces'
  - 'interfaces [Visual Basic], Visual Basic'
  - interfaces
  - 'interfaces [Visual Basic]'
ms.assetid: 61b06674-12c9-430b-be68-cc67ecee1f5b
---
# <a name="interfaces-visual-basic"></a>Arabirimler (Visual Basic)
*Arabirimleri* özellikleri, yöntemleri ve sınıfları uygulayan olayları tanımlayın. Arabirim Özellikleri yakından ilgili özellikleri, yöntemleri ve olayları küçük gruplar olarak tanımlamanızı sağlar; Varolan kodu tehlikeye atmadan, arabirimler için geliştirilmiş uygulamalar geliştirebilirsiniz çünkü bu uyumluluk sorunları azaltır. Ek arabirimleri ve uygulamalar geliştirerek, herhangi bir zamanda yeni özellikler ekleyebilirsiniz.  
  
 Neden arabirimleri sınıf devralma yerine kullanmak isteyebileceğiniz birkaç neden vardır:  
  
-   Arabirimleri daha iyi, uygulamalarınızın birçok nesne türlerini belirli işlevleri sağlamak için büyük olasılıkla ilgisi olmayan gereken durumlar için uygundur.  
  
-   Arabirimleri temel sınıfları daha esnek olduğu birden fazla arabirim uygulayabilir tek bir uygulamasını tanımlayabilirsiniz.  
  
-   Arabirimleri, uygulama temel sınıfından devralmak erişiminiz yok gibi durumlarda faydalıdır.  
  
-   Sınıf devralma kullanamadığınızda arabirimleri yararlı olur. Örneğin, yapılar sınıfı devralamaz ancak arabirimleri uygulayabilir.  
  
## <a name="declaring-interfaces"></a>Arabirimleri bildirme  
 Arabirim tanımları içinde içine `Interface` ve `End Interface` deyimleri. Aşağıdaki `Interface` deyimi, isteğe bağlı ekleyebilirsiniz `Inherits` listeleyen bir veya daha fazla devralınan arabirimi deyimi. `Inherits` Deyimleri bildiriminde açıklamaları dışındaki diğer tüm ifadeler gelmelidir. Arabirim tanımı kalan ifadeler olmalıdır `Event`, `Sub`, `Function`, `Property`, `Interface`, `Class`, `Structure`, ve `Enum` deyimleri. Arabirimleri, herhangi bir uygulama kodu veya uygulama kodu ile ilişkilendirilmiş ifadeler içeremez `End Sub` veya `End Property`.  
  
 Bir ad alanındaki arabirimi deyimleri olan `Friend` varsayılan olarak, ancak bunlar da açıkça olarak bildirilebilir `Public` veya `Friend`. Arabirimler, sınıflar, modüller, arabirimler içinde tanımlanan ve yapıları, `Public` varsayılan olarak, ancak bunlar da açıkça olarak bildirilebilir `Public`, `Friend`, `Protected`, veya `Private`.  
  
> [!NOTE]
>  `Shadows` Anahtar sözcüğü tüm arabirimi üyelerine uygulanabilir. `Overloads` Anahtar sözcüğü uygulanabilir `Sub`, `Function`, ve `Property` deyimleri bir arabirim tanımı içinde bildirilen. Ayrıca, `Property` deyimleri olabilir `Default`, `ReadOnly`, veya `WriteOnly` değiştiriciler. Diğer değiştiricilere hiçbiri —`Public`, `Private`, `Friend`, `Protected`, `Shared`, `Overrides`, `MustOverride`, veya `Overridable`— izin verilir. Daha fazla bilgi için [bildirim bağlamları ve varsayılan erişim düzeyleri](../../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Örneğin, aşağıdaki kod, bir işlev, bir özellik ve bir olay ile bir arabirim tanımlar.  
  
 [!code-vb[VbVbalrOOP#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#17)]  
  
## <a name="implementing-interfaces"></a>Arabirimleri uygulama  
 Visual Basic ayrılmış sözcük `Implements` iki şekilde kullanılır. `Implements` Deyimi, bir sınıf veya yapı bir arabirim uyguladığını belirtir. `Implements` Anahtar sözcüğü bir sınıf veya yapı üyesi belirli arabirim üyesini uyguladığını belirtir.  
  
### <a name="implements-statement"></a>Implements Deyimi  
 Bir sınıf veya yapı bir veya daha fazla arabirim uygularsa içermelidir `Implements` deyimi hemen sonra `Class` veya `Structure` deyimi. `Implements` Deyimi bir sınıf tarafından uygulanacak arabirim virgülle ayrılmış listesini gerektiriyor. Sınıf veya yapıda kullanarak tüm arabirim üyelerini uygulamalıdır `Implements` anahtar sözcüğü.  
  
### <a name="implements-keyword"></a>Implements anahtar sözcüğü  
 `Implements` Anahtar sözcüğünü gerektiriyor-uygulanacak arabirim üyeleri virgülle ayrılmış listesi. Genellikle, yalnızca tek bir arabirim üyesi belirtildi, ancak birden çok üye belirtebilirsiniz. Bir sınıf içinde Implements deyimi belirtilmesi gerekir arabirim adının bir arabirim üyesi belirtimi oluşur; bir süre; ve üye işlevi, özellik ya da uygulanacak olay adı. Bir arabirim üyesi uygulayan bir üyenin adını herhangi bir yasal tanımlayıcı kullanabilirsiniz ve bunlarla sınırlı değildir `InterfaceName_MethodName` Visual Basic'in önceki sürümlerinde kullanılan kural.  
  
 Örneğin, aşağıdaki kod nasıl adlı bir alt yordam gösterir `Sub1` bir arabirimin yöntemini uygulayan:  
  
 [!code-vb[VbVbalrOOP#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#69)]  
  
 Parametre türleri ve dönüş türleri uygulayan üyenin arabirimi arabirimi özelliği veya üye bildiriminde eşleşmelidir. Bir öğenin bir arabirim uygulamak için en yaygın arabirimi, aynı ada sahip bir üye ile önceki örnekte gösterildiği gibi yoludur.  
  
 Bir arabirim yönteminin uygulanması tanımlamak için de dahil olmak üzere örnek yöntem bildirimlerinde geçerlidir herhangi bir özniteliği kullanabilirsiniz `Overloads`, `Overrides`, `Overridable`, `Public`, `Private`, `Protected`, `Friend`, `Protected Friend`, `MustOverride`, `Default`, ve `Static`. `Shared` Özniteliği olmadığından geçerli bir örnek yöntemi yerine bir sınıf tanımlar.  
  
 Kullanarak `Implements`, birden çok yöntem aşağıdaki örnekteki gibi bir arabirim içinde tanımlanmış uygulayan tek bir yöntemi de yazabilirsiniz:  
  
 [!code-vb[VbVbalrOOP#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#70)]  
  
 Özel üye arabirim üyesini uygulamak için kullanabilirsiniz. Doğrudan nesne değişkenleri sınıf için kullanılabilir olmamasına rağmen bu üyede özel üye bir arabirim üyesi geliştirdiğinde arabirimi yoluyla kullanılabilir hale gelir.  
  
### <a name="interface-implementation-examples"></a>Arabirimi uygulama örnekleri  
 Bir arabirimi uygulayan sınıflar tüm özelliklerini, yöntemlerini ve olaylarını uygulamalıdır.  
  
 Aşağıdaki örnek, iki arabirim tanımlar. İkinci arabirimini `Interface2`, devralınan `Interface1` ve bir ek özellik ve yöntem tanımlar.  
  
 [!code-vb[VbVbalrOOP#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#39)]  
  
 Sonraki örnekte uygulayan `Interface1`, önceki örnekte tanımlanan arabirimi:  
  
 [!code-vb[VbVbalrOOP#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#40)]  
  
 Son örnek uygulayan `Interface2`, öğesinden devralınan bir yöntemi de dahil olmak üzere `Interface1`:  
  
 [!code-vb[VbVbalrOOP#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#41)]  
  
 Readwrite özelliğine sahip bir readonly özelliği uygulayabilirsiniz (diğer bir deyişle, uygulayan sınıfa salt okunur bildirmeniz gerekmez).  Arabirimi uygulama en az bildiren arabirimin üyeleri uygulamak taahhüt, ancak özelliğinizi yazılabilir olması izin verme gibi daha fazla işlevsellik sunabilir.  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[İzlenecek yol: Arabirimleri Oluşturma ve Uygulama](../../../../visual-basic/programming-guide/language-features/interfaces/walkthrough-creating-and-implementing-interfaces.md)|Tanımlama ve kendi arabirimini uygulayan işlemine götürür ayrıntılı bir yordam sağlar.|  
|[Genel Arabirimlerde Varyans](../../concepts/covariance-contravariance/variance-in-generic-interfaces.md)|Kovaryans ve kontravaryans in generic Interfaces açıklar ve .NET Framework'teki değişken genel arabirimler bir listesini sağlar.|
