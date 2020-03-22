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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400857"
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a>Bağımsız Değişkenleri Konuma ve Ada Göre Geçirme (Visual Basic)

Bir `Sub` `Function` yordamı aradiğinizde, bağımsız değişkenleri yordamın tanımında göründükleri sırayla konuma *göre* geçirebilir veya konuma bakılmaksızın bunları *adlarına*göre geçirebilirsiniz.

Bir bağımsız değişkeni ada göre geçtiğizde, bağımsız değişkenin beyan edilen`:=`adını ve ardından bir iki nokta üst üste ve eşit bir işaret (), ardından bağımsız değişken değerini belirtirsiniz. Adlandırılmış bağımsız değişkenleri istediğiniz sırada sağlayabilirsiniz.

Örneğin, aşağıdaki `Sub` yordam üç bağımsız değişken alır:

[!code-vb[SampleProcedure](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#1)]

Bu yordamı çağırdığınızda, bağımsız değişkenleri konuma, ada göre veya her ikisinin karışımını kullanarak sağlayabilirsiniz.

## <a name="passing-arguments-by-position"></a>Bağımsız Değişkenleri Konuma Göre Geçirme

`Display` Aşağıdaki örnekte gösterildiği gibi, konuma göre geçirilen ve virgülle sınırlandırılabilen bağımsız değişkenleriyle yöntemi çağırabilirsiniz:

[!code-vb[ByPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#2)]

Konumsal bağımsız değişken listesinde isteğe bağlı bir bağımsız değişkeni atlarsanız, virgülle yerini tutmanız gerekir. Aşağıdaki `age` örnek, `Display` bağımsız değişken olmadan yöntemi çağırır:

[!code-vb[ByPositionWithOptionalArgument](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#3)]

## <a name="passing-arguments-by-name"></a>Bağımsız Değişkenleri Ada Göre Geçirme

Alternatif olarak, aşağıdaki `Display` örnekte gösterildiği gibi, ad ile geçirilen ve virgülle de sınırlandırılmış bağımsız değişkenleri arayabilirsiniz:

[!code-vb[ByName](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#4)]

Bağımsız değişkenleri bu şekilde ada göre geçirme, özellikle birden fazla isteğe bağlı bağımsız değişkeni olan bir yordamı çağırdığınızda yararlıdır. Bağımsız değişkenleri ada göre sağlıyorsanız, eksik konumsal bağımsız değişkenleri belirtmek için ardışık virgül kullanmanız gerekmez. Bağımsız değişkenleri ada göre aktarmak, hangi bağımsız değişkenleri geçtiğinizü ve hangilerini atladığınızı izlemeyi de kolaylaştırır.

## <a name="mixing-arguments-by-position-and-by-name"></a>Konum ve Ada Göre Bağımsız Değişkenleri Karıştırma

Aşağıdaki örnekte gösterildiği gibi, bağımsız değişkenleri tek bir yordam çağrısında hem konuma hem de ada göre sağlayabilirsiniz:

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#5)]

Önceki örnekte, atlanan `age` bağımsız değişkenin yerini tutmak için fazladan virgül `birth` gerekmez, çünkü ada geçilir.

Visual Basic'in 15.5'ten önceki sürümlerinde, konum ve ad karışımıyla bağımsız değişkenler sağladığınızda, konumsal bağımsız değişkenlerin tümü önce gelmelidir. Bir bağımsız değişkeni ada göre tedarik ettikten sonra, kalan bağımsız değişkenlerden herhangi bir inanca göre geçirilmelidir.  Örneğin, `Display` yönteme aşağıdaki çağrı derleyici hata [BC30241 görüntüler: Adlandırılmış bağımsız değişken bekleniyor](../../../misc/bc30241.md).

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#6)]

Visual Basic 15.5 ile başlayarak, bitiş konumsal bağımsız değişkenleri doğru konumdaysa, konumsal bağımsız değişkenler adlandırılmış bağımsız değişkenleri izleyebilir. Visual Basic 15.5 altında derlenirse, `Display` yönteme yapılan önceki çağrı başarılı bir şekilde derlenir ve artık derleme hatası [OLUŞTURMAYAN BC30241.](../../../misc/bc30241.md)

Adı geçen ve konumlandırılmış bağımsız değişkenleri herhangi bir sırada karıştırma ve eşleştirme yeteneği, kodunuzu daha okunabilir hale getirmek için adlandırılmış bir bağımsız değişken kullanmak istediğinizde özellikle yararlıdır. Örneğin, aşağıdaki `Person` sınıf oluşturucu türünde `Person`iki bağımsız değişken `Nothing`gerektirir , her ikisi de olabilir .

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#7)]

Karışık adlandırılmış ve konumsal bağımsız değişkenler kullanarak kodun amacı `father` `mother` ve `Nothing`bağımsız değişkenlerin değeri açık hale getirmeye yardımcı olur:

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#8)]

Adlandırılmış bağımsız değişkenlerle konumsal bağımsız değişkenleri izlemek için Visual\*Basic projenize (.vbproj) aşağıdaki öğeyi eklemeniz gerekir:

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

Daha fazla bilgi için [Visual Basic dil sürümünü ayarlama ya](../../../language-reference/configure-language-version.md)da bkz.

## <a name="restrictions-on-supplying-arguments-by-name"></a>Ada Göre Bağımsız Değişken Sağlama Kısıtlamaları

Gerekli bağımsız değişkenleri girmemek için bağımsız değişkenleri adıyla geçiremezsiniz. Yalnızca isteğe bağlı bağımsız değişkenleri atlayabilirsiniz.

Bir parametre dizini ada göre geçiremezsiniz. Bunun nedeni, yordamı çağırdığınızda, parametre dizisi için belirsiz sayıda virgülle ayrılmış bağımsız değişken sağlamanızdır ve derleyici birden fazla bağımsız değişkeni tek bir adla ilişkilendiremez.

## <a name="see-also"></a>Ayrıca bkz.

- [Yordamlar](./index.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Nasıl yapılır: Bir Yordama Bağımsız Değişkenler Geçirme](./how-to-pass-arguments-to-a-procedure.md)
- [Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme](./passing-arguments-by-value-and-by-reference.md)
- [İsteğe Bağlı Parametreler](./optional-parameters.md)
- [Parametre Dizileri](./parameter-arrays.md)
- [Isteğe bağlı](../../../../visual-basic/language-reference/modifiers/optional.md)
- [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)
