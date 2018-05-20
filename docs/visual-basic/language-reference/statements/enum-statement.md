---
title: Enum Deyimi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Enum
helpviewer_keywords:
- enumerated constants [Visual Basic]
- Enum statement [Visual Basic]
- Private keyword [Visual Basic], Enum statements
- Public keyword [Visual Basic], in Enum statement
- variables [Visual Basic], enumeration
- constants [Visual Basic], enumerated
ms.assetid: a45e51f1-65ff-48e1-bf32-79130f137377
ms.openlocfilehash: 7cac4d5bde9ec617a1877a0605dc6dbab67ddf7f
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
---
# <a name="enum-statement-visual-basic"></a>Enum Deyimi (Visual Basic)
Numaralandırma bildirir ve üyeleri değerleri tanımlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
[ <attributelist> ] [ accessmodifier ]  [ Shadows ]   
Enum enumerationname [ As datatype ]   
   memberlist  
End Enum  
```  
  
## <a name="parts"></a>Bölümler  
  
-   `attributelist`  
  
     İsteğe bağlı. Bu numaralandırma uygulamak öznitelikler listesi. İçine almalısınız [öznitelik listesi](../../../visual-basic/language-reference/statements/attribute-list.md) açılı ayraç ("`<`"ve"`>`").  
  
     <xref:System.FlagsAttribute> Öznitelik, numaralandırma örneği değerini birden fazla numaralandırma üyeleri içerebilir ve her üye numaralandırma değeri bit alanında temsil ettiğini gösterir.  
  
-   `accessmodifier`  
  
     İsteğe bağlı. Bu numaralandırma hangi kod erişip belirtir. Aşağıdakilerden biri olabilir:  
  
    -   [Public](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [Private](../../../visual-basic/language-reference/modifiers/private.md)  
  
    - [Korumalı Friend](../../language-reference/modifiers/protected-friend.md)
    
    - [Özel korumalı](../../language-reference/modifiers/private-protected.md)

-   `Shadows`  
  
     İsteğe bağlı. Bu numaralandırma redeclares ve bir aynı adlı programlama öğesi ya da bir taban sınıf içinde aşırı yüklenmiş öğelerin gizler belirtir. Belirleyebileceğiniz [gölgeleri](../../../visual-basic/language-reference/modifiers/shadows.md) yalnızca numaralandırma, tüm üyeleri üzerinde değil.  
  
-   `enumerationname`  
  
     Gerekli. Numaralandırma adı. Geçerli adları hakkında daha fazla bilgi için bkz: [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
-   `datatype`  
  
     İsteğe bağlı. Numaralandırma ve tüm üyelerini veri türü.  
  
-   `memberlist`  
  
     Gerekli. Bu deyim içinde bildirilen üye sabitleri listesi. Birden çok üye bağımsız kaynak kodu satırlarda görünür.  
  
     Her `member` aşağıdaki söz dizimini ve bölümleri vardır: `[<attribute list>] member name [ = initializer ]`  
  
    |Bölümü|Açıklama|  
    |---|---|  
    |`membername`|Gerekli. Bu üye adı.|  
    |`initializer`|İsteğe bağlı. Derleme zamanında değerlendirilir ve bu üye için atanan ifade.|  
  
-   `End``Enum`  
  
     Sonlandırır `Enum` bloğu.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir mantıksal olarak birbiriyle ilişkili değişmeyen değerleri kümesi varsa, bunları bir numaralandırma birlikte tanımlayabilirsiniz. Bu numaralandırma ve değerlerine kolay üyelerini için anlamlı adlar sağlar. Numaralandırma üyeleri kodunuzda birçok yerde kullanın.  
  
 Numaralandırmalar kullanmanın avantajları şunlardır:  
  
-   Sırasını değiştirme veya numaraları yanlış yazmanız kaynaklanan hataları azaltır.  
  
-   Gelecekte değerlerini değiştirmek kolaylaştırır.  
  
-   Hataları görülecektir olasılığını anlamına gelen kod okumak daha kolay hale getirir.  
  
-   İleriye dönük uyumluluk sağlar. Numaralandırmalar kullanırsanız, kodunuzu gelecekte birinin üyesi adlarına karşılık gelen değerleri değişirse başarısız daha az olasıdır.  
  
 Numaralandırma bir ad, bir temel alınan veri türü ve bir üye kümesi vardır. Her üye bir sabiti temsil eder.  
  
 Sınıfı, yapısı, modül veya dışında herhangi bir yordam arabirimi düzeyinde bildirilen bir numaralandırma bir *üye numaralandırma*. Sınıfı, yapısı, modül veya onu tanımlandığı arabirimi bir üyesidir.  
  
 Üye numaralandırmalar gelen yerden kendi sınıfı, yapısı, modül veya arabirimi içinde erişilebilir. Kod bir sınıf dışında yapısı veya modülü bu sınıf, yapı veya modül adını bir üye numaralandırmanın adıyla nitelemeniz gerekir. Tam olarak nitelenmiş adlar ekleyerek kullanmaya gerek önleyebilirsiniz bir [içeri aktarmalar](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) kaynak dosyasına deyimi.  
  
 Sınıfı, yapısı, modül veya arabirim dışında ad alanı düzeyinde bildirilen numaralandırma göründüğü ad alanının bir üyesidir.  
  
 *Bildirimi bağlam* numaralandırma bir kaynak dosya, ad alanı, sınıf, yapısı, modül veya arabirimi olmalı ve bir yordam olamaz. Daha fazla bilgi için bkz: [bildirim bağlamları ve varsayılan erişim düzeyleri](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Öznitelikler için sabit bir bütün olarak ancak üyeleri için ayrı ayrı uygulayabilirsiniz. Bir öznitelik derlemenin meta verilerini bilgileri katkıda bulunur.  
  
## <a name="data-type"></a>Veri Türü  
 `Enum` Deyimi veri türü bir numaralandırmanın bildirebilirsiniz. Her üye sabit veri türünü alır. Belirleyebileceğiniz `Byte`, `Integer`, `Long`, `SByte`, `Short`, `UInteger`, `ULong`, veya `UShort`.  
  
 Belirtmezseniz, `datatype` numaralandırma için her üye veri türünü alır. kendi `initializer`. Her ikisini de belirtirseniz, `datatype` ve `initializer`, veri türü `initializer` dönüştürülebilir olmalıdır `datatype`. Ne `datatype` ya da `initializer` varsa, veri türü için varsayılan `Integer`.  
  
## <a name="initializing-members"></a>Üyeleri başlatma  
 `Enum` Deyimi içinde seçilen üyeleri içeriğini başlatma `memberlist`. Kullandığınız `initializer` üyesine atanacak bir ifade sağlamak için.  
  
 Belirtmezseniz, `initializer` bir üye için Visual Basic, sıfır ya da başlatır (ilk ise `member` içinde `memberlist`), ya da tek hemen önceki, daha büyük bir değere `member`.  
  
 Her sağlanan ifade `initializer` değişmez değerleri, önceden tanımlanmış diğer sabitleri ve zaten, önceki bu numaralandırma üyesi de dahil olmak üzere tanımlanan numaralandırma üyeleri herhangi bir bileşimi olabilir. Bu öğeler birleştirmek için aritmetik ve mantıksal işleçleri kullanabilirsiniz.  
  
 Değişkenleri veya işlevleri kullanamazsınız `initializer`. Ancak, dönüşüm anahtar sözcükleri gibi kullanabilir `CByte` ve `CShort`. Aynı zamanda `AscW` bir sabit ile çağırırsanız `String` veya `Char` derleme zamanında değerlendirilebilir beri bağımsız değişkeni.  
  
 Numaralandırmalar kayan nokta değerlerine sahip olamaz. Üye bir kayan nokta değer atanırsa ve `Option Strict` , bir derleyici hatası oluşursa ayarlanır. Varsa `Option Strict` kapalıysa, değeri için otomatik olarak dönüştürülür `Enum` türü.  
  
 Temel alınan veri türü için izin verilen aralığın bir üyesinin değerini aşması durumunda veya herhangi bir üyesi temel alınan veri türü tarafından izin verilen en yüksek değere başlatmak, derleyici bir hata bildirir.  
  
## <a name="modifiers"></a>Değiştiriciler  
 Sınıfı, yapısı, modül ve arabirim üye numaralandırmalar varsayılan genel erişim için. Erişim değiştiricileri ile erişim düzeylerine göre ayarlayabilirsiniz. Namespace üye numaralandırmalar varsayılan friend erişim. Ortak, ancak özel veya korumalı erişim düzeylerine göre ayarlayabilirsiniz. Daha fazla bilgi için bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 Tüm numaralandırma üyeleri ortak erişimi vardır ve bunlar üzerinde hiçbir erişim değiştiricileri kullanamazsınız. Numaralandırma daha kısıtlı erişim düzeyi varsa, ancak belirtilen numaralandırma erişim düzeyi önceliklidir.  
  
 Varsayılan olarak, tüm numaralandırma türleri ve onların alanları sabitleri. Bu nedenle `Shared`, `Static`, ve `ReadOnly` numaralandırma veya üyeleri bildirirken anahtar sözcükler kullanılamaz.  
  
## <a name="assigning-multiple-values"></a>Birden çok değerler atama  
 Numaralandırmalar genellikle birbirini dışlayan değerleri temsil eder. Ekleyerek <xref:System.FlagsAttribute> özniteliğini `Enum` bildirimi, bunun yerine atayabilirsiniz birden çok değer numaralandırması örneğine. <xref:System.FlagsAttribute> Özniteliği, numaralandırma bayrakları diğer bir deyişle, bir dizi bir bit alanı olarak değerlendirilmesi belirtir. Bunlar adlandırılır *Bitsel* numaralandırmalar.  
  
 Ne zaman bildirdiğiniz numaralandırma kullanarak <xref:System.FlagsAttribute> özniteliği öneririz, 2, 1, 2, 4, 8, 16 ve vb. tabanların değerlerini kullanın. Ayrıca, "None" değeri 0 olan bir üyenin adını olmasını öneririz. Ek yönergeler için bkz: <xref:System.FlagsAttribute> ve <xref:System.Enum>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte nasıl kullanılacağını gösterir `Enum` deyimi. Üye olarak adlandırılır Not `EggSizeEnum.Medium`, değil de `Medium`.  
  
 [!code-vb[VbEnumsTask#41](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_1.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte yöntemi dışında `Egg` sınıfı. Bu nedenle, `EggSizeEnum` olarak tam olarak nitelenmiş `Egg.EggSizeEnum`.  
  
 [!code-vb[VbEnumsTask#42](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_2.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır `Enum` ilgili kümesini tanımlamak için deyimi adlı sabit değerleri. Bu durumda, bir veritabanı için veri girişi formları tasarlama tercih edebileceğiniz renkleri değerlerdir.  
  
 [!code-vb[VbEnumsTask#30](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_3.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, pozitif ve negatif sayıları içeren değerleri gösterir.  
  
 [!code-vb[VbEnumsTask#31](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_4.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, bir `As` yan tümcesini belirtmek için kullanılan `datatype` bir numaralandırma.  
  
 [!code-vb[VbEnumsTask#6](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_5.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte bir bit düzeyinde numaralandırma kullanmayı gösterir. Bit düzeyinde numaralandırması örneğine birden çok değer atanabilir. `Enum` Bildirimi içerir <xref:System.FlagsAttribute> numaralandırma bayrakları kümesi olarak işlenebilir gösteren özniteliği.  
  
 [!code-vb[VbEnumsTask#61](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_6.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir numaralandırma yineler. Kullanır <xref:System.Enum.GetNames%2A> numaralandırma içinden üye adlarının dizisini almak için yöntemini ve <xref:System.Enum.GetValues%2A> üye değerleri dizisi alınamadı.  
  
 [!code-vb[VbEnumsTask#51](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_7.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Enum>  
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>  
 [Const Deyimi](../../../visual-basic/language-reference/statements/const-statement.md)  
 [Dim Deyimi](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [Örtük ve Açık Dönüştürmeler](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [Tür Dönüştürme İşlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Sabitler ve Sabit Listeleri](../../../visual-basic/language-reference/constants-and-enumerations.md)
