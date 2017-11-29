---
title: "Structure Yapısı"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Structure
- Structure
helpviewer_keywords:
- user-defined types [Visual Basic], Structure statement
- compound data types [Visual Basic]
- Structure keyword [Visual Basic]
- Structure statement [Visual Basic]
- UDT (user-defined types)
- types [Visual Basic], user-defined
ms.assetid: 9bd1deea-2a89-4cdc-812c-6dcbb947c391
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 43211bb10793acf3bfe0c1d7a35791114170ee7d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="structure-statement"></a>Structure Yapısı
Bir yapı adını bildirir ve tanımını değişkenleri, özellikleri, olayları ve yapısı oluşur yordamları sunar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ Partial ] _  
Structure name [ ( Of typelist ) ]  
    [ Implements interfacenames ]  
    [ datamemberdeclarations ]  
    [ methodmemberdeclarations ]  
End Structure  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`attributelist`|İsteğe bağlı. Bkz: [öznitelik listesi](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|İsteğe bağlı. Aşağıdakilerden biri olabilir:<br /><br /> -   [Ortak](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [Korumalı](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Arkadaş](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Özel](../../../visual-basic/language-reference/modifiers/private.md)<br />-   `Protected Friend`<br /><br /> Bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|İsteğe bağlı. Bkz: [gölgeleri](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`Partial`|İsteğe bağlı. Kısmi bir yapının tanımını gösterir. Bkz: [kısmi](../../../visual-basic/language-reference/modifiers/partial.md).|  
|`name`|Gerekli. Bu yapı adı. Bkz: [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`Of`|İsteğe bağlı. Bu genel yapısı olduğunu belirtir.|  
|`typelist`|Kullanırsanız, gerekli [,](../../../visual-basic/language-reference/statements/of-clause.md) anahtar sözcüğü. Bu yapı türü parametrelerinin listesi. Bkz: [yazın listesi](../../../visual-basic/language-reference/statements/type-list.md).|  
|`Implements`|İsteğe bağlı. Bu yapı bir veya daha fazla arabirimin üyelerini uyguladığını gösterir. Bkz: [uygulayan deyimi](../../../visual-basic/language-reference/statements/implements-statement.md).|  
|`interfacenames`|Kullanırsanız, gerekli `Implements` deyimi. Bu yapı uygulayan arabirimleri adları.|  
|`datamemberdeclarations`|Gerekli. Sıfır veya daha fazla `Const`, `Dim`, `Enum`, veya `Event` bildirme deyimleri *veri üyeleri* yapısı.|  
|`methodmemberdeclarations`|İsteğe bağlı. Sıfır veya daha fazla bildirimlerini `Function`, `Operator`, `Property`, veya `Sub` olarak hizmet yordamları *yöntemi üyeleri* yapısı.|  
|`End Structure`|Gerekli. Sonlandırır `Structure` tanımı.|  
  
## <a name="remarks"></a>Açıklamalar  
 `Structure` Deyimi özelleştirebileceğiniz bir bileşik değeri türü tanımlar. A *yapısı* Genelleştirme önceki sürümlerinde Visual Basic, kullanıcı tanımlı tür (UDT) değil. Daha fazla bilgi için bkz: [yapıları](../../../visual-basic/programming-guide/language-features/data-types/structures.md).  
  
 Yapıları sınıflar olarak aynı özelliklerin çoğunu destekler. Örneğin, yapıları özellikleri ve yordamları olabilir, arabirimleri uygulayabilir ve bunlar oluşturucular parametreli. Ancak, devralma, bildirimler ve kullanımı gibi alanlarda yapılar ve sınıflar arasında önemli farklılıklar vardır. Ayrıca, sınıflar başvuru türleri ve yapıları değer türleri. Daha fazla bilgi için bkz: [yapılar ve sınıflar](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md).  
  
 Kullanabileceğiniz `Structure` yalnızca ad alanı veya düzeyinde modülü. Yani *bildirimi bağlam* bir yapı bir kaynak dosya, ad alanı, sınıf, yapısı, modül veya arabirimi olmalı ve bir yordam veya blok olamaz. Daha fazla bilgi için bkz: [bildirim bağlamları ve varsayılan erişim düzeyleri](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Yapıları varsayılan [arkadaş](../../../visual-basic/language-reference/modifiers/friend.md) erişim. Erişim değiştiricileri ile erişim düzeylerine göre ayarlayabilirsiniz. Daha fazla bilgi için bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="rules"></a>Kurallar  
  
-   **İç içe geçirme.** Başka bir yapısında tanımlayabilirsiniz. Dış yapısı adlı *yapısı içeren*, ve iç yapısı adlı bir *yapısı iç içe geçmiş*. Ancak, iç içe geçmiş yapısı üyeleri içeren yapısı erişilemiyor. Bunun yerine, iç içe geçmiş yapısı veri türünde bir değişken bildirmeniz gerekir.  
  
-   **Üye bildirimi.** Her bir yapı üyesi bildirmeniz gerekir. Yapı üyesi olamaz [korumalı](../../../visual-basic/language-reference/modifiers/protected.md) veya `Protected Friend` hiçbir şey bir yapısından devrettiği için. Yapı kendisi, ancak olabilir `Protected` veya `Protected Friend`.  
  
     Sıfır veya daha fazla paylaşılmayan değişkenleri ya da bir yapı paylaşılmayan de olaylar bildirebilirsiniz. Bunlardan bazıları paylaşılmayan olsa bile, yalnızca sabitleri, özellikleri ve yordamları, sahip olamaz.  
  
-   **Başlatma.** Herhangi bir yapı bildiriminden bir parçası olarak paylaşılmayan veri üyesi değerini başlatılamıyor. Parametreli Oluşturucusu yapısına yoluyla böyle bir veri üyesi başlatmak, veya yapısı örneği oluşturduktan sonra üyesine bir değere atayın.  
  
-   **Devralma.** Bir yapı herhangi bir türünden dışında devral olamaz <xref:System.ValueType>, hangi tüm yapıları devral gelen. Özellikle, bir yapı başka bir devralma olamaz.  
  
     Kullanamazsınız [Inherits deyimi](../../../visual-basic/language-reference/statements/inherits-statement.md) belirtmek için bir yapı tanımında bile <xref:System.ValueType>.  
  
-   **Uygulaması.** Yapı kullanıyorsa [Implements deyimi](../../../visual-basic/language-reference/statements/implements-statement.md), belirttiğiniz her arabirim tarafından tanımlanan her üye uygulamalıdır `interfacenames`.  
  
-   **Varsayılan özellik.** Bir yapıyı en çok bir özellik olarak belirtebilirsiniz, *varsayılan özellik*kullanarak [varsayılan](../../../visual-basic/language-reference/modifiers/default.md) değiştiricisi. Daha fazla bilgi için bkz: [varsayılan](../../../visual-basic/language-reference/modifiers/default.md).  
  
## <a name="behavior"></a>Davranış  
  
-   **Erişim düzeyi.** Bir yapı her üye kendi erişim düzeyi ile bildirebilir. Varsayılan olarak tüm yapı üyeleri [ortak](../../../visual-basic/language-reference/modifiers/public.md) erişim. Erişim değiştiricileri ile bunların erişim düzeylerini ayarlamak olsa bile yapısı daha kısıtlı erişim düzeyi varsa, bu otomatik olarak erişim üyeleri için sınırlar olduğunu unutmayın.  
  
-   **Kapsamı.** Kendi içeren ad alanı, sınıf, yapı veya modülü boyunca kapsamdaki bir yapıdır.  
  
     Her bir yapı üyenin kapsamını tüm yapısıdır.  
  
-   **Yaşam süresi.** Bir yapı kendisini bir yaşam süresi yok. Bunun yerine, bu yapıyı her örneğinin diğer tüm örneklerini bağımsız bir yaşam süresi vardır.  
  
     Tarafından oluşturulan bir örneği ömrü başlar bir [New işleci](../../../visual-basic/language-reference/operators/new-operator.md) yan tümcesi. Tutan değişken ömrü sona erdiğinde sona erer.  
  
     Yapısı örneği ömrü genişletemezsiniz. Statik yapısı işlevselliğe yaklaşık bir modül tarafından sağlanır. Daha fazla bilgi için bkz: [Module deyimi](../../../visual-basic/language-reference/statements/module-statement.md).  
  
     Yapı üyeleri nasıl ve nerede bildirilir bağlı olarak ömürleri vardır. Daha fazla bilgi için bkz: "Ömrü" [Class deyimi](../../../visual-basic/language-reference/statements/class-statement.md).  
  
-   **Niteliğe.** Kod bir yapı dışında bir üyenin adını yapıyı adıyla nitelemeniz gerekir.  
  
     Kod iç içe geçmiş yapısı içinde bir programlama öğesi nitelenmemiş bir başvuru yaparsa, Visual Basic öğe için ilk iç içe geçmiş yapısında, ardından içeren yapısını ve benzeri en dıştaki içeren öğesine arar. Daha fazla bilgi için bkz: [bildirilmiş öğelere başvurular](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
-   **Bellek tüketimi.** Tüm bileşik veri türleri gibi güvenli bir şekilde birbirine üyeleri nominal depolama ayrılmasını ekleyerek bir yapı toplam bellek tüketimi hesaplanamıyor. Ayrıca, depolama bellekte sırasını siparişinizi bildirimiyle aynı olduğunu güvenle varsayalım olamaz. Bir yapı depolama düzenini denetlemeye ihtiyacınız varsa, uygulamadan <xref:System.Runtime.InteropServices.StructLayoutAttribute> özniteliğini `Structure` deyimi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır `Structure` çalışana ait ilgili veri kümesini tanımlamak için deyimi. Kullanımı gösterilmiştir `Public`, `Friend`, ve `Private` veri öğelerini duyarlılığını yansıtacak şekilde üyeleri. Ayrıca, yordam, özellik ve olay üyeleri gösterir.  
  
 [!code-vb[VbVbalrStatements#57](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/structure-statement_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Class deyimi](../../../visual-basic/language-reference/statements/class-statement.md)  
 [Interface deyimi](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [Module deyimi](../../../visual-basic/language-reference/statements/module-statement.md)  
 [Dim deyimi](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [Const deyimi](../../../visual-basic/language-reference/statements/const-statement.md)  
 [Enum deyimi](../../../visual-basic/language-reference/statements/enum-statement.md)  
 [Event deyimi](../../../visual-basic/language-reference/statements/event-statement.md)  
 [Operator deyimi](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Property deyimi](../../../visual-basic/language-reference/statements/property-statement.md)  
 [Yapılar ve sınıflar](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
