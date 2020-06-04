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
ms.openlocfilehash: 021805508a8a053ccc8fab6f1013109bece4b6f2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404777"
---
# <a name="declare-statement"></a>Declare Deyimi

Dış dosyada uygulanan bir yordama başvuru bildirir.

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

|Terim|Tanım|
|---|---|
|`attributelist`|İsteğe bağlı. Bkz. [öznitelik listesi](attribute-list.md).|
|`accessmodifier`|İsteğe bağlı. Aşağıdakilerden biri olabilir:<br /><br /> -   [Geneldir](../modifiers/public.md)<br />-   [Korunamadı](../modifiers/protected.md)<br />-   [Dost](../modifiers/friend.md)<br />-   [Özelleştirme](../modifiers/private.md)<br />- [Korumalı arkadaş](../modifiers/protected-friend.md)<br />- [Özel korumalı](../modifiers/private-protected.md)<br /><br /> [Visual Basic erişim düzeylerine](../../programming-guide/language-features/declared-elements/access-levels.md)bakın.|
|`Shadows`|İsteğe bağlı. Bkz. [gölgeler](../modifiers/shadows.md).|
|`charsetmodifier`|İsteğe bağlı. Karakter kümesi ve dosya arama bilgilerini belirtir. Aşağıdakilerden biri olabilir:<br /><br /> -   [ANSI](../modifiers/ansi.md) (varsayılan)<br />-   [Kodlamaları](../modifiers/unicode.md)<br />-   [Otomatik](../modifiers/auto.md)|
|`Sub`|İsteğe bağlı, ancak ya da `Sub` `Function` görünür olmalıdır. Dış yordamın bir değer döndürmediğini belirtir.|
|`Function`|İsteğe bağlı, ancak ya da `Sub` `Function` görünür olmalıdır. Dış yordamın bir değer döndürdüğünü gösterir.|
|`name`|Gereklidir. Bu dış başvurunun adı. Daha fazla bilgi için bkz. [bildirilmemiş öğe adları](../../programming-guide/language-features/declared-elements/declared-element-names.md).|
|`Lib`|Gereklidir. `Lib`Dış yordam içeren dış dosyayı (dll veya kod kaynağı) tanımlayan bir yan tümce tanıtır.|
|`libname`|Gereklidir. Belirtilen yordamı içeren dosyanın adı.|
|`Alias`|İsteğe bağlı. Tanımlanmakta olan yordamın, içinde belirtilen ad ile dosyasında belirlenemediğini belirtir `name` . Kimliğini ' de belirtin `aliasname` .|
|`aliasname`|`Alias`Anahtar sözcüğünü kullanmanız gerekir. İki şekilde yordamı tanımlayan dize:<br /><br /> İçindeki yordamın, tırnak işaretleri () içinde giriş noktası adı `""`<br /><br /> -veya-<br /><br /> Bir sayı işareti ( `#` ), ardından yordamın giriş noktasının dosya içindeki sıra sayısını belirten bir tamsayı|
|`parameterlist`|Yordam parametreleri alırsa gereklidir. Bkz. [parametre listesi](parameter-list.md).|
|`returntype`|`Function`Belirtilmişse ve `Option Strict` ise gereklidir `On` . Yordamın döndürdüğü değerin veri türü.|

## <a name="remarks"></a>Açıklamalar

Bazen, bir dosyada (örneğin, bir DLL veya kod kaynağı gibi) tanımlanan bir yordamı projenizin dışında çağırmanız gerekir. Bunu yaptığınızda, Visual Basic derleyicisinin yordamın nerede olduğu, nasıl tanımlandığı, arama sırası ve dönüş türü ve kullandığı dize karakter kümesi gibi yordamı çağırması için gereken bilgilere erişimi yoktur. İfade, bir `Declare` dış yordama bir başvuru oluşturur ve bu gerekli bilgileri sağlar.

`Declare`Yalnızca modül düzeyinde kullanabilirsiniz. Bu, bir dış başvurunun *bildirim bağlamının* bir sınıf, yapı veya modül olması ve kaynak dosya, ad alanı, arabirim, yordam veya blok olması anlamına gelir. Daha fazla bilgi için bkz. [bildirim bağlamları ve varsayılan erişim düzeyleri](declaration-contexts-and-default-access-levels.md).

Dış başvurular varsayılan olarak [genel](../modifiers/public.md) erişime sahiptir. Erişim değiştiricilerini kullanarak erişim düzeylerini ayarlayabilirsiniz.

## <a name="rules"></a>Kurallar

- **Özelliklerine.** Öznitelikleri bir dış başvuruya uygulayabilirsiniz. Uyguladığınız herhangi bir öznitelik, dış dosyada değil yalnızca projenizde etkilidir.

- **İlerine.** Dış yordamlar örtük olarak [paylaşılır](../modifiers/shared.md). `Shared`Dış başvuru bildirirken anahtar sözcüğünü kullanamaz ve paylaşılan durumunu değiştiremezsiniz.

  Dış yordam, geçersiz kılma, arabirim üyeleri uygulama veya olayları işleme alanına katılamaz. Buna uygun olarak,,,,, `Overrides` `Overridable` `NotOverridable` `MustOverride` `Implements` veya `Handles` anahtar sözcüğünü bir `Declare` bildirimde kullanamazsınız.

- **Dış yordam adı.** Bu dış başvuruya, `name` kendi dış dosyası () içinde yordamın giriş noktası adı ile aynı adı (içinde) vermeniz gerekmez `aliasname` . `Alias`Giriş noktası adını belirtmek için bir yan tümce kullanabilirsiniz. Bu, dış yordamın Visual Basic ayrılmış değiştirici veya bir değişken, yordam veya aynı kapsamda başka bir programlama öğesiyle aynı ada sahipse yararlı olabilir.

  > [!NOTE]
  > Çoğu dll 'deki giriş noktası adları büyük/küçük harfe duyarlıdır.

- **Dış yordam numarası.** Alternatif olarak, `Alias` dış dosyanın dışarı aktarma tablosundaki giriş noktasının sıra sayısını belirtmek için bir yan tümce kullanabilirsiniz. Bunu yapmak için `aliasname` bir sayı işaretiyle ( `#` ) başlarsınız. Bu, dış yordam adındaki herhangi bir karaktere Visual Basic izin verilmiyorsa veya dış dosya yordamı bir ad olmadan dışarı aktardığında yararlı olabilir.

## <a name="data-type-rules"></a>Veri türü kuralları

- **Parametre veri türleri.** `Option Strict`İse `On` , içindeki her parametrenin veri türünü belirtmeniz gerekir `parameterlist` . Bu, herhangi bir veri türü veya bir numaralandırma, yapı, sınıf veya arabirimin adı olabilir. İçinde `parameterlist` , `As` her parametreye geçirilecek bağımsız değişkenin veri türünü belirtmek için bir yan tümce kullanırsınız.

  > [!NOTE]
  > Dış yordam .NET Framework için yazılmadığından, veri türlerinin karşılık geldiği konusunda dikkatli olmanız gerekir. Örneğin, bir parametre ile bir Visual Basic 6,0 yordamına dış başvuru bildirirseniz `Integer` (Visual Basic 6,0 ' de 16 bit), `Short` `Declare` Bu, Visual Basic 16 bit tamsayı türü olduğundan, karşılık gelen bağımsız değişkeni deyimde olduğu gibi tanımlamalısınız. Benzer şekilde, `Long` Visual Basic 6,0 ' de farklı bir veri genişliğine sahiptir ve `Date` farklı şekilde uygulanır.

- **Dönüş veri türü.** Dış yordam bir ve ise, `Function` `Option Strict` `On` çağırma koduna döndürülen değerin veri türünü belirtmeniz gerekir. Bu, herhangi bir veri türü veya bir numaralandırma, yapı, sınıf veya arabirimin adı olabilir.

  > [!NOTE]
  > Visual Basic Derleyicisi, veri türlerinizin dış yordamla uyumlu olduğunu doğrulamaz. Bir uyuşmazlık varsa, ortak dil çalışma zamanı çalışma zamanında bir <xref:System.Runtime.InteropServices.MarshalDirectiveException> özel durum oluşturur.

- **Varsayılan veri türleri.** `Option Strict`İse `Off` ve ' de bir parametrenin veri türünü belirtmezseniz `parameterlist` , Visual Basic derleyici karşılık gelen bağımsız değişkeni [nesne veri türüne](../data-types/object-data-type.md)dönüştürür. Benzer şekilde, belirtmezseniz `returntype` , derleyici döndürülen veri türünü de alır `Object` .

  > [!NOTE]
  > Farklı bir platformda yazılmış olabilecek bir dış yordam ile ilgilenirken, veri türleri hakkında varsayımlar yapmak veya bunların varsayılan olmasına izin vermek tehlikeli olabilir. Varsa, her parametrenin ve dönüş değerinin veri türünü belirtmek çok daha güvenlidir. Bu, kodunuzun okunabilirliğini de artırır.

## <a name="behavior"></a>Davranış

- **Kapsam.** Dış başvuru, sınıf, yapı veya modül genelinde kapsamdadır.

- **Süre.** Dış başvuru, bildirildiği sınıf, yapı veya modülle aynı yaşam süresine sahiptir.

- **Dış yordam çağırma.** Bir ya da yordamını, bir değer döndürürse ya da bir `Function` `Sub` değer döndürmezse bir [Call deyiminde](call-statement.md) belirterek kullanarak bir veya yordamı çağıran şekilde bir dış yordam çağırmanız gerekir.

  Bağımsız değişkenleri, bildiriminde tarafından belirtilen şekilde dış yordama geçirebilirsiniz `parameterlist` `Declare` . Parametrelerin dış dosyada ilk olarak nasıl bildirildiği dikkate alma. Benzer şekilde, bir dönüş değeri varsa, tam olarak ifadesinde belirtilen şekilde kullanın `returntype` `Declare` .

- **Karakter kümeleri.** `charsetmodifier`Dış yordamı çağırdığında Visual Basic dizelerin nasıl sıralaması gerektiğini belirtebilirsiniz. `Ansi`Değiştirici, tüm DIZELERI ANSI değerlerine göre sıralamak için Visual Basic yönlendirir ve `Unicode` değiştirici onu tüm dizeleri Unicode değerlerine göre sıralamak için yönlendirir. `Auto`Değiştirici, dış başvuruya göre .NET Framework kurallarına göre veya belirtilmişse dizeleri sıralama Visual Basic yönlendirir `name` `aliasname` . Varsayılan değer: `Ansi`.

  `charsetmodifier`Ayrıca, Visual Basic dış yordamın dış dosyası içinde nasıl araması gerektiğini de belirtir. `Ansi``Unicode`Ayrıca, arama sırasında adını değiştirmeden bunu aramak için doğrudan Visual Basic. `Auto`çalışma zamanı platformunun temel karakter kümesini belirlemede Visual Basic yönlendirir ve büyük olasılıkla dış yordam adını şu şekilde değiştirebilir:

  - Windows 95, Windows 98 veya Windows Millennium Edition gibi bir ANSI platformunda, önce ad değişikliğine sahip olmayan dış yordama bakmanız gerekir. Başarısız olursa, dış yordam adının sonuna "A" ekleyin ve tekrar arama yapın.

  - Windows NT, Windows 2000 veya Windows XP gibi bir Unicode platformunda, önce ad değişikliğine sahip olmayan dış yordama bakmanız gerekir. Başarısız olursa, dış yordam adının sonuna "W" ekleyin ve tekrar arama yapın.

- **Mekanizmadır.** Visual Basic, dış yordamları çözümlemek ve erişmek için .NET Framework *Platform çağırma* (PInvoke) mekanizmasını kullanır. `Declare`Ve <xref:System.Runtime.InteropServices.DllImportAttribute> sınıfı bu mekanizmayı otomatik olarak kullanır ve herhangi bir PInvoke bilgisine ihtiyacınız yoktur. Daha fazla bilgi için bkz. [Izlenecek yol: Windows API 'Leri çağırma](../../programming-guide/com-interop/walkthrough-calling-windows-apis.md).

> [!IMPORTANT]
> Dış yordam ortak dil çalışma zamanının (CLR) dışında çalışırsa, bu, yönetilmeyen bir *koddur*. Örneğin, bir Windows API işlevi veya bir COM yöntemi gibi bir yordamı çağırdığınızda, uygulamanızı güvenlik risklerine maruz kalabilirsiniz. Daha fazla bilgi için bkz. [yönetilmeyen kod Için güvenli kodlama yönergeleri](https://docs.microsoft.com/previous-versions/dotnet/framework/security/secure-coding-guidelines-for-unmanaged-code).

## <a name="example"></a>Örnek

Aşağıdaki örnek, `Function` geçerli kullanıcı adını döndüren bir yordamın dış başvurusunu bildirir. Ardından, `GetUserNameA` yordamın bir parçası olarak dış yordamı çağırır `getUser` .

[!code-vb[VbVbalrStatements#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#15)]

## <a name="example"></a>Örnek

, <xref:System.Runtime.InteropServices.DllImportAttribute> Yönetilmeyen koddaki işlevleri kullanmanın alternatif bir yolunu sağlar. Aşağıdaki örnek, bir ifade kullanmadan içeri aktarılan bir işlevi bildirir `Declare` .

[!code-vb[VbVbalrStatements#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#16)]

[!code-vb[VbVbalrStatements#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#1)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.ErrObject.LastDllError%2A>
- [Imports Deyimi (.NET Ad Alanı ve Türü)](imports-statement-net-namespace-and-type.md)
- [AddressOf İşleci](../operators/addressof-operator.md)
- [Function Deyimi](function-statement.md)
- [Sub Deyimi](sub-statement.md)
- [Parametre Listesi](parameter-list.md)
- [Call Deyimi](call-statement.md)
- [İzlenecek yol: Windows API'lerini Çağırma](../../programming-guide/com-interop/walkthrough-calling-windows-apis.md)
