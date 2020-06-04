---
title: Enum Deyimi
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
ms.openlocfilehash: 976cc68d67c69ec86918962ab2dd3406d15aed9a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404738"
---
# <a name="enum-statement-visual-basic"></a>Enum Deyimi (Visual Basic)

Bir sabit listesi bildirir ve üyelerinin değerlerini tanımlar.

## <a name="syntax"></a>Sözdizimi

```vb
[ <attributelist> ] [ accessmodifier ]  [ Shadows ]
Enum enumerationname [ As datatype ]
   memberlist
End Enum
```

## <a name="parts"></a>Bölümler

- `attributelist`

  İsteğe bağlı. Bu sabit listesi için uygulanan özniteliklerin listesi. [Öznitelik listesini](attribute-list.md) açılı ayraçlar (" `<` " ve " `>` ") içine almalısınız.

  <xref:System.FlagsAttribute>Özniteliği, sabit listesinin bir örneğinin değerinin birden çok numaralandırma üyesi içerebileceğini ve her üyenin numaralandırma değerindeki bir bit alanını temsil ettiğini gösterir.

- `accessmodifier`

  İsteğe bağlı. Bu numaralandırmaya erişebilecek kodu belirtir. Aşağıdakilerden biri olabilir:

  - [Geneldir](../modifiers/public.md)

  - [Korunamadı](../modifiers/protected.md)

  - [Dost](../modifiers/friend.md)

  - [Özelleştirme](../modifiers/private.md)

  - [Protected Friend](../modifiers/protected-friend.md)

  - [Özel korumalı](../modifiers/private-protected.md)

- `Shadows`

  İsteğe bağlı. Bu sabit listesinin, bir temel sınıfta aynı adlı programlama öğesi veya aşırı yüklenmiş öğeler kümesini yeniden bildirdiğini ve gizlediğini belirtir. Her üye üzerinde değil, yalnızca Numaralandırmadaki [gölgeleri](../modifiers/shadows.md) belirtebilirsiniz.

- `enumerationname`

  Gereklidir. Sabit listesinin adı. Geçerli adlar hakkında daha fazla bilgi için bkz. [bildirilmemiş öğe adları](../../programming-guide/language-features/declared-elements/declared-element-names.md).

- `datatype`

  İsteğe bağlı. Numaralandırmanın ve tüm üyelerinin veri türü.

- `memberlist`

  Gereklidir. Bu bildirimde bildirildiği üye sabitlerinin listesi. Tek tek kaynak kodu satırlarında birden çok üye görüntülenir.

  Her birinin `member` aşağıdaki söz dizimi ve parçaları vardır:`[<attribute list>] member name [ = initializer ]`

  |Bölüm|Description|
  |---|---|
  |`membername`|Gereklidir. Bu üyenin adı.|
  |`initializer`|İsteğe bağlı. Derleme zamanında değerlendirilen ve bu üyeye atanan ifade.|

- `End` `Enum`

  Bloğu sonlandırır `Enum` .

## <a name="remarks"></a>Açıklamalar

Mantıksal olarak birbirleriyle ilgili değişmeyen bir değerler kümesi varsa, bunları bir numaralandırmada birlikte tanımlayabilirsiniz. Bu, sabit listesi ve üyeleri için değerlerinden daha kolay anımsanacak anlamlı adlar sağlar. Daha sonra, sabit listesi üyelerini kodunuzda birçok yerde kullanabilirsiniz.

Numaralandırmalar kullanmanın avantajları şunlardır:

- Dışarı veya hatalı yazma numaralarının neden olduğu hataları azaltır.

- Gelecekte değerlerin değiştirilmesini kolaylaştırır.

- Kodun daha kolay okunmasını sağlar, bu da hataların tanıtılmasından daha az olabilir.

- İleriye dönük uyumluluğu sağlar. Numaralandırmalar kullanıyorsanız, gelecekte birisinin üye adlarına karşılık gelen değerleri değiştirmesinin ardından kodunuzun başarısız olma olasılığı düşüktür.

Bir numaralandırma bir ada, temel alınan veri türüne ve bir üye kümesine sahiptir. Her üye bir sabiti temsil eder.

Sınıf, yapı, modül veya arabirim düzeyinde tanımlanan ve herhangi bir yordamın dışında bir numaralandırma, bir *üye numaralandırmadır*. Bunu bildiren sınıf, yapı, modül veya arabirimin bir üyesidir.

Üye numaralandırmalara, sınıfları, yapısı, modülü veya arabirimi içinde herhangi bir yerden erişilebilir. Bir sınıf, yapı veya modülün dışındaki kodun, bir üye sabit listesinin adını bu sınıf, yapı veya modülün adı ile nitelemesi gerekir. Kaynak dosyaya bir [Içeri aktarmalar](imports-statement-net-namespace-and-type.md) açıklaması ekleyerek tam nitelikli adlar kullanma gereksinimini ortadan kaldırabilirsiniz.

Herhangi bir sınıf, yapı, modül veya arabirim dışında, ad alanı düzeyinde belirtilen bir sabit listesi, göründüğü ad alanının bir üyesidir.

Bir numaralandırma için *Bildirim bağlamı* bir kaynak dosya, ad alanı, sınıf, yapı, modül veya arabirim olmalıdır ve bir yordam olamaz. Daha fazla bilgi için bkz. [bildirim bağlamları ve varsayılan erişim düzeyleri](declaration-contexts-and-default-access-levels.md).

Öznitelikleri bir numaralandırmaya bir bütün olarak uygulayabilir, ancak üyelerine tek tek atayabilirsiniz. Bir öznitelik, bilgileri derlemenin meta verilerine katkıda bulunur.

## <a name="data-type"></a>Veri Türü

`Enum`İfade, bir numaralandırmanın veri türünü bildirebilirler. Her üye, numaralandırmanın veri türünü alır. ,,,,, `Byte` `Integer` ,, Veya belirtebilirsiniz `Long` `SByte` `Short` `UInteger` `ULong` `UShort` .

`datatype`Sabit listesi için belirtmezseniz, her üye öğesinin veri türünü alır `initializer` . Hem hem de belirtirseniz `datatype` `initializer` , veri türü `initializer` öğesine dönüştürülebilir olmalıdır `datatype` . Ne yoksa `datatype` ne de `initializer` yoksa, veri türü varsayılan olarak olur `Integer` .

## <a name="initializing-members"></a>Üyeler başlatılıyor

`Enum`İfade, içindeki seçili üyelerin içeriğini başlatabilir `memberlist` . `initializer`Üyeye atanacak bir ifade sağlamak için kullanırsınız.

`initializer`Bir üye için belirtmeyin, Visual Basic bunu sıfıra (ilk `member` içinde ise `memberlist` ) veya bir değerden daha büyük bir değere, hemen öncesinde gelen bir değere başlatır `member` .

Her birinde sağlanan ifade `initializer` , herhangi bir sabit değer, önceden tanımlanmış diğer sabitler ve bu numaralandırmanın önceki bir üyesi dahil, zaten tanımlanmış olan sabit listesi üyeleri olabilir. Bu tür öğeleri birleştirmek için aritmetik ve mantıksal işleçler kullanabilirsiniz.

İçindeki değişkenleri veya işlevleri kullanamazsınız `initializer` . Ancak, ve gibi dönüştürme anahtar sözcüklerini kullanabilirsiniz `CByte` `CShort` . `AscW` `String` `Char` Derleme zamanında değerlendirilebileceğinizden, bu değeri bir sabit veya bağımsız değişkenle birlikte çağırırsanız de kullanabilirsiniz.

Numaralandırmalar kayan nokta değerlerine sahip olamaz. Bir üyeye kayan nokta değeri atanmışsa ve `Option Strict` Açık olarak ayarlanırsa, bir derleyici hatası oluşur. `Option Strict`Kapalıysa, değer otomatik olarak `Enum` türüne dönüştürülür.

Bir üyenin değeri, temel alınan veri türü için izin verilen aralığı aşarsa veya herhangi bir üyeyi temel alınan veri türü tarafından izin verilen en yüksek değere başlattığınızda, derleyici bir hata bildirir.

## <a name="modifiers"></a>Değiştiriciler

Sınıf, yapı, modül ve arabirim üyesi numaralandırmalar, genel erişim için varsayılan. Erişim değiştiricilerini kullanarak erişim düzeylerini ayarlayabilirsiniz. Ad alanı üyesi numaralandırmalar arkadaş erişimi için varsayılan değer. Erişim düzeylerini herkese açık olarak ayarlayabilir, ancak özel veya korumalı olamaz. Daha fazla bilgi için bkz. [Visual Basic erişim düzeyleri](../../programming-guide/language-features/declared-elements/access-levels.md).

Tüm numaralandırma üyelerinin ortak erişimi vardır ve bunlar üzerinde herhangi bir erişim değiştiricilerini kullanamazsınız. Ancak, numaralandırmanın kendisi daha kısıtlı erişim düzeyine sahipse, belirtilen numaralandırma erişim düzeyi önceliklidir.

Varsayılan olarak, tüm numaralandırmalar türlerdir ve alanları sabittir. Bu nedenle `Shared` ,, `Static` ve `ReadOnly` anahtar sözcükleri bir numaralandırma veya üyeleri bildirirken kullanılamaz.

## <a name="assigning-multiple-values"></a>Birden çok değer atama

Numaralandırmalar genellikle birbirini dışlayan değerleri temsil eder. <xref:System.FlagsAttribute>Özniteliği `Enum` bildirime ekleyerek, bunun yerine sabit listesinin bir örneğine birden çok değer atayabilirsiniz. <xref:System.FlagsAttribute>Özniteliği, numaralandırmanın bir bit alanı, yani bir bayrak kümesi olarak değerlendirilip değerlendirilmediğini belirtir. Bunlara *bit düzeyinde* numaralandırmalar denir.

Özniteliği kullanarak bir numaralandırma bildirdiğinizde <xref:System.FlagsAttribute> , değerler için 2, bu, 1, 2, 4, 8, 16, vb. üslerini kullanmanızı öneririz. Ayrıca "none" değerinin değeri 0 olan üyenin adı olması önerilir. Ek yönergeler için bkz <xref:System.FlagsAttribute> . ve <xref:System.Enum> .

## <a name="example"></a>Örnek

Aşağıdaki örnek, ifadesinin nasıl kullanılacağını göstermektedir `Enum` . Üyenin olarak adlandırıldığına ve farklı şekilde olduğunu unutmayın `EggSizeEnum.Medium` `Medium` .

[!code-vb[VbEnumsTask#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#41)]

## <a name="example"></a>Örnek

Aşağıdaki örnekteki yöntemi `Egg` sınıfının dışındadır. Bu nedenle, `EggSizeEnum` tam olarak nitelenir `Egg.EggSizeEnum` .

[!code-vb[VbEnumsTask#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#42)]

## <a name="example"></a>Örnek

Aşağıdaki örnek, `Enum` ilgili bir adlandırılmış sabit değer kümesini tanımlamak için ifadesini kullanır. Bu durumda, değerler, bir veritabanı için veri girişi formları tasarlamayı seçebileceğiniz renklerdir.

[!code-vb[VbEnumsTask#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#30)]

## <a name="example"></a>Örnek

Aşağıdaki örnek, hem pozitif hem de negatif sayı içeren değerleri gösterir.

[!code-vb[VbEnumsTask#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#31)]

## <a name="example"></a>Örnek

Aşağıdaki örnekte, bir `As` sabit listesini belirtmek için bir yan tümce kullanılır `datatype` .

[!code-vb[VbEnumsTask#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#6)]

## <a name="example"></a>Örnek

Aşağıdaki örnek bit düzeyinde numaralandırmanın nasıl kullanılacağını göstermektedir. Bit düzeyinde numaralandırma örneğine birden çok değer atanabilir. `Enum`Bildirimi, <xref:System.FlagsAttribute> numaralandırmanın bir dizi bayrak olarak değerlendirileceğini gösteren özniteliğini içerir.

[!code-vb[VbEnumsTask#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#61)]

## <a name="example"></a>Örnek

Aşağıdaki örnek bir numaralandırma boyunca yinelenir. <xref:System.Enum.GetNames%2A>Numaralandırmadaki üye adları dizisini almak ve <xref:System.Enum.GetValues%2A> bir dizi üye değeri almak için yöntemini kullanır.

[!code-vb[VbEnumsTask#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#51)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Enum>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- [Const Deyimi](const-statement.md)
- [Dim Deyimi](dim-statement.md)
- [Örtük ve Açık Dönüştürmeler](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Tür Dönüştürme İşlevleri](../functions/type-conversion-functions.md)
- [Sabitler ve numaralandırmalar](../constants-and-enumerations.md)
