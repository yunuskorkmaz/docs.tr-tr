---
title: Bağımsız Değişkenleri Konuma ve Ada Göre Geçirme
ms.date: 02/01/2018
helpviewer_keywords:
- arguments [Visual Basic], passing by name
- procedures [Visual Basic], arguments
- := passing arguments
- procedure arguments
- Visual Basic code, procedures
- named arguments [Visual Basic], passing arguments
- arguments [Visual Basic], passing by position
- Function procedures [Visual Basic], passing arguments
- named parameters [Visual Basic], passing arguments
- named arguments
- passing parameters [Visual Basic], named parameter arguments
- passing parameters [Visual Basic], by position
- procedures [Visual Basic], calling
- named parameters
- Sub procedures [Visual Basic], passing arguments
- argument passing
- passing parameters [Visual Basic], by name
- argument passing [Visual Basic], by position
- arguments [Visual Basic], listing by name
ms.assetid: 1ad7358f-1da9-48da-a95b-f3c7ed41eff3
ms.openlocfilehash: b6588335f7634cc87a9fc14cbfc4ba80baad1abb
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352615"
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a>Bağımsız Değişkenleri Konuma ve Ada Göre Geçirme (Visual Basic)

Bir `Sub` veya `Function` yordamını çağırdığınızda, bağımsız değişkenleri, yordamın tanımında göründükleri *sırada — ya* da *konuma göre geçirebilirsiniz, sonra*da konuma göre geçiş yapabilirsiniz.

Bir bağımsız değişkeni adına göre geçirdiğinizde, bağımsız değişkenin belirtilen adını, ardından iki nokta üst üste ve eşittir işaretini (`:=`) ve ardından bağımsız değişken değerini belirtirsiniz. Adlandırılmış bağımsız değişkenleri istediğiniz sırada sağlayabilirsiniz.

Örneğin, aşağıdaki `Sub` yordamı üç bağımsız değişkeni alır:

[!code-vb[SampleProcedure](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#1)]

Bu yordamı çağırdığınızda, bağımsız değişkenleri konuma, ada veya her ikisinin bir karışımını kullanarak sağlayabilirsiniz.

## <a name="passing-arguments-by-position"></a>Bağımsız değişkenleri konuma göre geçirme

Aşağıdaki örnekte gösterildiği gibi, konum ve virgülle ayrılmış bağımsız değişkenleriyle `Display` yöntemi çağırabilirsiniz:

[!code-vb[ByPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#2)]

Konumsal bağımsız değişken listesinde isteğe bağlı bir bağımsız değişkeni atlarsanız, onun yerini virgül ile tutmanız gerekir. Aşağıdaki örnek, `age` bağımsız değişkeni olmadan `Display` yöntemini çağırır:

[!code-vb[ByPositionWithOptionalArgument](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#3)]

## <a name="passing-arguments-by-name"></a>Bağımsız değişkenleri ada göre geçirme

Alternatif olarak, aşağıdaki örnekte gösterildiği gibi, ada göre geçirilen bağımsız değişkenlerle `Display` çağırabilirsiniz ve virgülle da ayrılır:

[!code-vb[ByName](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#4)]

Bu şekilde bağımsız değişkenleri bu şekilde geçirmek, birden fazla isteğe bağlı bağımsız değişkeni olan bir yordamı çağırdığınızda özellikle yararlıdır. Ada göre bağımsız değişkenler sağlarsanız, eksik Konumsal bağımsız değişkenleri belirtmek için ardışık virgüller kullanmanız gerekmez. Bağımsız değişkenleri ada göre geçirmek, geçirdiğiniz bağımsız değişkenleri ve hangilerinin dışarıda geçtiğini izlemeyi kolaylaştırır.

## <a name="mixing-arguments-by-position-and-by-name"></a>Bağımsız değişkenleri konuma ve ada göre karıştırma

Aşağıdaki örnekte gösterildiği gibi tek bir yordam çağrısında hem konuma hem de ada göre bağımsız değişkenler sağlayabilirsiniz:

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#5)]

Yukarıdaki örnekte, `birth` adı ile geçirildiğinden atlanan `age` bağımsız değişkeninin yerini tutmak için ek virgül gerekmez.

15,5 ' den önceki Visual Basic sürümlerinde, konum ve ad karışımı ile bağımsız değişkenleri sağlarsanız, Konumsal bağımsız değişkenlerin hepsi ilk olarak gelmelidir. Ada göre bir bağımsız değişken sağlarsanız, kalan tüm bağımsız değişkenlerin tümünün adına göre geçirilmesi gerekir.  Örneğin, `Display` yöntemine yapılan aşağıdaki çağrı derleyici hatası [BC30241: adlandırılmış bağımsız değişken bekleniyor](../../../misc/bc30241.md).

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#6)]

Visual Basic 15,5 ' den başlayarak, konum bağımsız değişkenleri bitiş Konumsal bağımsız değişkenleri doğru konumundayken adlandırılmış bağımsız değişkenler izleyebilir. Visual Basic 15,5 altında derlenirse, `Display` yöntemine yapılan önceki çağrı başarıyla derlenir ve artık derleyici hatası [BC30241](../../../misc/bc30241.md)oluşturmaz.

Adlandırılmış ve Konumsal bağımsız değişkenleri herhangi bir sırada karıştırabilme ve eşleştirme özelliği, kodunuzun daha okunaklı olması için adlandırılmış bir bağımsız değişken kullanmak istediğinizde özellikle yararlıdır. Örneğin, aşağıdaki `Person` sınıf oluşturucusu `Person`türünde iki bağımsız değişken gerektirir, ikisi de `Nothing`olabilir.

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#7)]

Karışık adlandırılmış ve Konumsal bağımsız değişkenlerin kullanılması, `father` ve `mother` bağımsız değişkenlerin değeri `Nothing`olduğunda kodun amacını açık hale getirir.

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#8)]

Adlandırılmış bağımsız değişkenlerle Konumsal bağımsız değişkenleri izlemek için, Visual Basic projesi (\*. vbproj) dosyanıza aşağıdaki öğeyi eklemeniz gerekir:

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

Daha fazla bilgi için bkz. [Visual Basic dil sürümünü ayarlama](../../../language-reference/configure-language-version.md).

## <a name="restrictions-on-supplying-arguments-by-name"></a>Ada göre bağımsız değişken sağlamaya yönelik kısıtlamalar

Gerekli bağımsız değişkenleri girmekten kaçınmak için bağımsız değişkenleri ada göre geçiremezsiniz. Yalnızca isteğe bağlı bağımsız değişkenleri atlayabilirsiniz.

Bir parametre dizisini ada göre geçiremezsiniz. Bunun nedeni, yordamı çağırdığınızda parametre dizisi için sınırsız sayıda virgülle ayrılmış bağımsız değişken sağlarsınız ve derleyici birden fazla bağımsız değişkeni tek bir adla ilişkilendiremez.

## <a name="see-also"></a>Ayrıca bkz.

- [Yordamlar](./index.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Nasıl yapılır: Bir Yordama Bağımsız Değişkenler Geçirme](./how-to-pass-arguments-to-a-procedure.md)
- [Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme](./passing-arguments-by-value-and-by-reference.md)
- [İsteğe Bağlı Parametreler](./optional-parameters.md)
- [Parametre Dizileri](./parameter-arrays.md)
- [Optional](../../../../visual-basic/language-reference/modifiers/optional.md)
- [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)
