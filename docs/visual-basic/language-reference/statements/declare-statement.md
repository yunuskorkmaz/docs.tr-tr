---
title: Declare Deyimi
ms.date: 07/20/2015
f1_keywords:
- vb.Declare
- vb.Lib
- vb.Any
helpviewer_keywords:
- Lib keyword [Visual Basic]
- declaring procedures [Visual Basic], Declare statement
- functions [Visual Basic], function procedures
- declarations [Visual Basic], procedures
- procedures [Visual Basic], declaration
- procedures [Visual Basic], external
- Alias keyword [Visual Basic]
- external references [Visual Basic], Visual Basic
- DLLs, declaring procedures
- Declare statement [Visual Basic]
- declarations [Visual Basic], external
- Visual Basic code, Function procedures
- As keyword [Visual Basic], in Declare statement
- resources [Visual Basic], declaring
- Public keyword [Visual Basic], Declare statement
- platform invoke, Visual Basic external references
- Sub procedures [Visual Basic], declarations
- APIs, declaring API functions
- Visual Basic code, Sub procedures
- Function procedures [Visual Basic], declaring
ms.assetid: d3f21fb0-b804-4c99-97ed-583b23894cf1
ms.openlocfilehash: 9895709076634ce156ba9d1009f79ba7ddd2ba56
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646380"
---
# <a name="declare-statement"></a>Declare Deyimi

Harici bir dosyada uygulanan bir yordam için bir başvuru bildirir.

## <a name="syntax"></a>Sözdizimi

```vb
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ Overloads ] _
Declare [ charsetmodifier ] [ Sub ] name Lib "libname" _
[ Alias "aliasname" ] [ ([ parameterlist ]) ]
' -or-
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ Overloads ] _
Declare [ charsetmodifier ] [ Function ] name Lib "libname" _
[ Alias "aliasname" ] [ ([ parameterlist ]) ] [ As returntype ]
```

## <a name="parts"></a>Bölümler

|Sözleşme Dönemi|Tanım|
|---|---|
|`attributelist`|İsteğe bağlı. Bkz. [Öznitelik Listesi](../../../visual-basic/language-reference/statements/attribute-list.md).|
|`accessmodifier`|İsteğe bağlı. Aşağıdakilerden biri olabilir:<br /><br /> -   [Kamu](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [Korumalı](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Arkadaş](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Özel](../../../visual-basic/language-reference/modifiers/private.md)<br />- [Korunan Arkadaş](../../language-reference/modifiers/protected-friend.md)<br />- [Özel Korumalı](../../language-reference/modifiers/private-protected.md)<br /><br /> [Visual Basic'teki Erişim düzeylerine](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)bakın.|
|`Shadows`|İsteğe bağlı. Bkz. [Gölgeler](../../../visual-basic/language-reference/modifiers/shadows.md).|
|`charsetmodifier`|İsteğe bağlı. Karakter kümesi ni ve dosya arama bilgilerini belirtir. Aşağıdakilerden biri olabilir:<br /><br /> -   [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md) (varsayılan)<br />-   [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)<br />-   [Otomatik](../../../visual-basic/language-reference/modifiers/auto.md)|
|`Sub`|İsteğe bağlı, `Function` ancak ya da `Sub` görünmesi gerekir. Dış yordamın bir değer döndürmediğini gösterir.|
|`Function`|İsteğe bağlı, `Function` ancak ya da `Sub` görünmesi gerekir. Dış yordamın bir değer döndürür olduğunu gösterir.|
|`name`|Gereklidir. Bu dış başvurunun adı. Daha fazla bilgi için, [Bildirilen Öğe Adları'na](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)bakın.|
|`Lib`|Gereklidir. Harici bir `Lib` yordam içeren dış dosyayı (DLL veya kod kaynağı) tanımlayan bir yan tümce yi tanıtır.|
|`libname`|Gereklidir. Beyan edilen yordamı içeren dosyanın adı.|
|`Alias`|İsteğe bağlı. Beyan edilen yordamın dosyasında belirtilen adla tanımlanamayacağını `name`gösterir. Kimliğini ' de `aliasname`belirtin.|
|`aliasname`|Anahtar sözcüğü `Alias` kullanıyorsanız gereklidir. Yordamı iki şekilde tanımlayan dize:<br /><br /> Dosya içinde yordamın giriş noktası adı,`""`tırnak içinde ( )<br /><br /> -veya-<br /><br /> Bir sayı`#`işareti ( ) ve ardından dosya içindeki yordamın giriş noktasının ordinal numarasını belirten bir tamsayı|
|`parameterlist`|Yordam parametreleri alıyorsa gereklidir. Bkz. [Parametre Listesi](../../../visual-basic/language-reference/statements/parameter-list.md).|
|`returntype`|Belirtilirse `Function` ve `Option Strict` `On`. Yordam tarafından döndürülen değerin veri türü.|

## <a name="remarks"></a>Açıklamalar

Bazen projenizin dışında bir dosyada tanımlanan bir yordamı (DLL veya kod kaynağı gibi) çağırmanız gerekir. Bunu yaptığınızda, Visual Basic derleyicisi yordamı doğru çağırmak için gereken bilgilere (yordamın nerede bulunduğu, nasıl tanımlandığı, çağrı sırası ve dönüş türü ve kullandığı string karakter kümesi gibi) erişimi yoktur. İfade, `Declare` harici bir prosedüre atıfta bulunarak gerekli bilgileri sağlar.

Yalnızca modül `Declare` düzeyinde kullanabilirsiniz. Bu, dış başvuru nun *bildirim bağlamının* bir sınıf, yapı veya modül olması gerektiği ve kaynak dosyası, ad alanı, arabirim, yordam veya blok olamayacağı anlamına gelir. Daha fazla bilgi için [Bildirim Bağlamları ve Varsayılan Erişim Düzeyleri'ne](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)bakın.

Dış başvurular varsayılan [olarak Genel](../../../visual-basic/language-reference/modifiers/public.md) erişime. Erişim değiştiriciler ile erişim düzeylerini ayarlayabilirsiniz.

## <a name="rules"></a>Kurallar

- **Öznitelik.** Öznitelikleri harici bir başvuruya uygulayabilirsiniz. Uyguladığınız herhangi bir öznitelik, dış dosyada değil, yalnızca projenizde etkili olur.

- **Değiştirici.** Dış yordamlar örtülü olarak [paylaşılır.](../../../visual-basic/language-reference/modifiers/shared.md) Dış başvuru `Shared` bildirirken anahtar sözcüğü kullanamazsınız ve paylaşılan durumunu değiştiremezsiniz.

  Harici bir yordam geçersiz kılmaya katılamaz, arabirim üyelerini uygulayamaz veya olayları işleyemez. `Overrides`Buna göre, bir `Overridable` `NotOverridable` `MustOverride` `Implements` `Handles` `Declare` deyimde , , , , , veya anahtar kelime kullanamazsınız.

- **Dış Yordam Adı.** Bu dış başvuruya yordamın dış dosyasındaki `name`giriş noktası adı (in) ile aynı`aliasname`adı vermeniz gerekmez. Giriş noktası `Alias` adını belirtmek için bir yan tümce kullanabilirsiniz. Bu, dış yordam, Visual Basic ayrılmış bir değiştirici veya aynı kapsamdaki bir değişken, yordam veya başka bir programlama öğesi ile aynı ada sahipse yararlı olabilir.

  > [!NOTE]
  > Çoğu DL'deki giriş noktası adları büyük/küçük harf duyarlıdır.

- **Dış Yordam Numarası.** Alternatif olarak, dış `Alias` dosyanın dış dosyanın dış tablosundaki giriş noktasının ordinal numarasını belirtmek için bir yan tümce kullanabilirsiniz. Bunu yapmak için, `aliasname` bir sayı`#`işareti ile başlar ( ). Bu, Visual Basic'te dış yordam adındaki herhangi bir karaktere izin verilmiyorsa veya dış dosya yordamı ad olmadan dışa aktaracaksa yararlı olabilir.

## <a name="data-type-rules"></a>Veri Türü Kuralları

- **Parametre Veri Türleri.** Ise, `Option Strict` her parametrenin veri türünü `parameterlist` `On` Bu herhangi bir veri türü veya numaralandırma, yapı, sınıf veya arabirim adı olabilir. Içinde, `parameterlist`her `As` parametreye geçirilecek bağımsız değişkenin veri türünü belirtmek için bir yan tümce kullanırsınız.

  > [!NOTE]
  > .NET Framework için dış yordam yazılmadıysa, veri türlerinin karşılık verdiğine dikkat etmelisiniz. Örneğin, bir parametre (Visual Basic 6.0'da `Integer` 16 bit) olan bir Visual Basic 6.0 yordamına `Short` harici `Declare` bir başvuru bildirirseniz, Visual Basic'teki 16 bit tamsayı türü olduğundan, ilgili bağımsız değişkeni deyimdeki gibi tanımlamanız gerekir. Benzer şekilde, `Long` Visual Basic 6.0'da farklı `Date` bir veri genişliğine sahiptir ve farklı şekilde uygulanır.

- **Veri Türünü Döndür.** Dış yordam a `Function` ise `Option Strict` `On`ve , arama koduna döndürülen değerin veri türünü belirtmeniz gerekir. Bu herhangi bir veri türü veya numaralandırma, yapı, sınıf veya arabirim adı olabilir.

  > [!NOTE]
  > Visual Basic derleyicisi, veri tiplerinizin dış yordamla uyumlu olduğunu doğrulamaz. Bir uyuşmazlık varsa, ortak dil çalışma zamanı çalışma <xref:System.Runtime.InteropServices.MarshalDirectiveException> zamanında bir özel durum oluşturur.

- **Varsayılan Veri Türleri.** Eğer `Option Strict` `Off` ve bir parametrenin veri türünü `parameterlist`belirtmezseniz, Visual Basic derleyicisi ilgili bağımsız değişkeni Nesne Veri [Türüne](../../../visual-basic/language-reference/data-types/object-data-type.md)dönüştürür. Benzer şekilde, belirtmezseniz, `returntype`derleyici döndürücü veri `Object`türünü .

  > [!NOTE]
  > Farklı bir platformda yazılmış olabilecek harici bir yordamla uğraşıyorsanız, veri türleri hakkında herhangi bir varsayımda bulunmak veya bunların varsayılan olarak uygulanmasına izin vermek tehlikelidir. Varsa, her parametrenin ve iade değerinin veri türünü belirtmek çok daha güvenlidir. Bu, kodunuzun okunabilirliğini de artırır.

## <a name="behavior"></a>Davranış

- **Kapsam.** Dış başvuru, sınıfı, yapısı veya modülü boyunca kapsam içindedir.

- **Ömür boyu.** Harici bir başvuru, beyan edildiği sınıf, yapı veya modülle aynı kullanım ömrüne sahiptir.

- **Harici Yordam'ı arama.** Harici yordamı, bir değer döndürürse bir ifadede kullanarak veya bir değer döndürmezse [Çağrı Ekstresinde](../../../visual-basic/language-reference/statements/call-statement.md) belirterek, bir `Function` `Sub` yordamı çağırdığınız şekilde çağırırsınız.

  Bağımsız değişkenleri, `parameterlist` deyimde tam olarak `Declare` belirtildiği şekilde dış yordama geçirirsiniz. Parametrelerin dış dosyada ilk olarak nasıl beyan edildiğini dikkate almayın. Benzer şekilde, bir iade değeri varsa, `returntype` `Declare` tam olarak deyiminde belirtildiği şekilde kullanın.

- **Karakter Setleri.** Visual Basic'in `charsetmodifier` dış yordamı aradığında dizeleri nasıl bağlaması gerektiğini belirtebilirsiniz. Değiştirici Visual `Ansi` Basic'i tüm dizeleri ANSI değerlerine `Unicode` bağlamaya yönlendirir ve değiştirici tüm dizeleri Unicode değerlerine göre şerife yönlendirir. Değiştirici Visual `Auto` Basic'i dış başvuruya `name`veya `aliasname` belirtilmişse .NET Framework kurallarına göre dize lere yönlendirir. Varsayılan değer: `Ansi`.

  `charsetmodifier`ayrıca Visual Basic'in dış dosyaiçindeki dış yordamı nasıl bakması gerektiğini belirtir. `Ansi`ve `Unicode` hem doğrudan Visual Basic arama sırasında adını değiştirmeden bakmak için. `Auto`Çalışma zamanı platformunun temel karakter kümesini belirlemek ve dış yordam adını aşağıdaki gibi değiştirmek için Visual Basic'i yönlendirir:

  - Windows 95, Windows 98 veya Windows Millennium Edition gibi bir ANSI platformunda, önce ad değişikliği olmadan dış yordamı arayın. Bu başarısız olursa, dış yordam adının sonuna "A" ekleyip yeniden arayın.

  - Windows NT, Windows 2000 veya Windows XP gibi bir Unicode platformunda, önce ad değişikliği olmadan dış yordamı arayın. Bu başarısız olursa, dış yordam adının sonuna "W" ekleyip yeniden arayın.

- **Mekanizması.** Visual Basic, dış yordamları çözmek ve erişmek için .NET Framework *platform invoke* (PInvoke) mekanizmasını kullanır. Deyim `Declare` ve <xref:System.Runtime.InteropServices.DllImportAttribute> sınıf hem otomatik olarak bu mekanizmayı kullanmak ve PInvoke herhangi bir bilgiye gerek yoktur. Daha fazla bilgi için [Walkthrough: Windows API'lerini arama](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md).

> [!IMPORTANT]
> Dış yordam ortak dil çalışma zamanı (CLR) dışında çalışırsa, *bu yönetilmeyen koddur.* Böyle bir yordamı (örneğin bir Windows API işlevi veya COM yöntemi) çağırdığınızda, uygulamanızı güvenlik risklerine maruz bırakabilirsiniz. Daha fazla bilgi için, [Yönetilmeyen Kodlar için Güvenli Kodlama Yönergeleri'ne](https://docs.microsoft.com/previous-versions/dotnet/framework/security/secure-coding-guidelines-for-unmanaged-code)bakın.

## <a name="example"></a>Örnek

Aşağıdaki örnek, geçerli kullanıcı adını `Function` döndüren bir yordam için harici bir başvuru bildirir. Daha sonra `GetUserNameA` `getUser` yordamın bir parçası olarak dış yordamı çağırır.

[!code-vb[VbVbalrStatements#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#15)]

## <a name="example"></a>Örnek

Yönetilen <xref:System.Runtime.InteropServices.DllImportAttribute> olmayan kodda işlevleri kullanmanın alternatif bir yolunu sağlar. Aşağıdaki örnek, bir `Declare` deyim kullanmadan içe aktarılan bir işlevi bildirir.

[!code-vb[VbVbalrStatements#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#16)]

[!code-vb[VbVbalrStatements#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#1)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.ErrObject.LastDllError%2A>
- [Imports Deyimi (.NET Ad Alanı ve Türü)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [AddressOf İşleci](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Fonksiyon Bildirimi](../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Parametre Listesi](../../../visual-basic/language-reference/statements/parameter-list.md)
- [Call Deyimi](../../../visual-basic/language-reference/statements/call-statement.md)
- [İzlenecek yol: Windows API'lerini Çağırma](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
