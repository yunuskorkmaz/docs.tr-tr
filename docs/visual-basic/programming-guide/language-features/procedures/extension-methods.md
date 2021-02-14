---
description: 'Daha fazla bilgi edinin: uzantı yöntemleri (Visual Basic)'
title: Uzantı Metotları
ms.date: 07/20/2015
f1_keywords:
- vb.ExtensionMethods
helpviewer_keywords:
- extending data types [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: b8020aae-374d-46a9-bcb7-8cc2390b93b6
ms.openlocfilehash: 5a1482502b144524c0be90e1c83a38f49b4a4d26
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100434361"
---
# <a name="extension-methods-visual-basic"></a>Uzantı Yöntemleri (Visual Basic)

Uzantı yöntemleri, geliştiricilerin zaten yeni bir türetilmiş tür oluşturmadan tanımlanmış olan veri türlerine özel işlevler eklemesini sağlar. Uzantı yöntemleri, var olan türün bir örnek yöntemi gibi çağrılabilecek bir yöntem yazmayı mümkün hale getirir.

## <a name="remarks"></a>Açıklamalar

Genişletme yöntemi yalnızca bir `Sub` yordam veya `Function` yordam olabilir. Uzantı özelliğini, alanı veya olayı tanımlayamazsınız. Tüm genişletme yöntemlerinin ad alanından uzantı özniteliğiyle işaretlenmesi `<Extension>` <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> ve bir [modülde](../../../language-reference/statements/module-statement.md)tanımlanması gerekir. Bir uzantı yöntemi bir modül dışında tanımlanmışsa, Visual Basic Derleyicisi Hata [BC36551](../../../misc/bc36551.md)oluşturur, "uzantı yöntemleri yalnızca modüllerde tanımlanabilir".

Bir genişletme yöntemi tanımındaki ilk parametre, yöntemin hangi veri türünde genişletiğini belirtir. Yöntemi çalıştırıldığında, ilk parametre yöntemini çağıran veri türü örneğine bağlanır.

`Extension`Özniteliği yalnızca bir Visual Basic [`Module`](../../../language-reference/statements/module-statement.md) , veya için uygulanabilir [`Sub`](../../../language-reference/statements/sub-statement.md) [`Function`](../../../language-reference/statements/function-statement.md) . Bunu bir veya a 'ya uygularsanız `Class` `Structure` Visual Basic Derleyicisi Hata [BC36550](../../../language-reference/error-messages/extension-attribute-can-be-applied-only-to-module-sub-or-function-declarations.md)oluşturuyor, "' Extension" özniteliği yalnızca ' Module ', ' Sub ' veya ' function ' bildirimlerine uygulanabilir.

## <a name="example"></a>Örnek

Aşağıdaki örnek, `Print` veri türü için bir uzantı tanımlar <xref:System.String> . Yöntemi `Console.WriteLine` bir dizeyi göstermek için kullanır. Yönteminin parametresi, `Print` `aString` yönteminin sınıfını genişlettiğini belirler <xref:System.String> .

[!code-vb[VbVbalrExtensionMethods#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/StringExtensions.vb#1)]

Uzantı metodu tanımının uzantı özniteliğiyle işaretlendiğine dikkat edin `<Extension()>` . Yöntemin tanımlandığı modülün işaretlenmesi isteğe bağlıdır, ancak her genişletme yöntemi işaretlenmelidir. <xref:System.Runtime.CompilerServices> Uzantı özniteliğine erişebilmek için içeri aktarılmalıdır.

Uzantı yöntemleri yalnızca modüller içinde bildirilemez. Genellikle, bir uzantı yönteminin tanımlandığı modül, çağrıldığı bir modül olarak değildir. Bunun yerine, uzantı yöntemini içeren modül içeri aktarıldıysa, kapsama getirmek için içeri aktarılır. İçeren modül `Print` kapsam içinde olduğunda, yöntemi bağımsız değişken içermeyen sıradan bir örnek yöntemi gibi çağrılabilir, örneğin `ToUpper` :

[!code-vb[VbVbalrExtensionMethods#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class1.vb#2)]

Sonraki örnek, `PrintAndPunctuate` için de bir uzantısıdır <xref:System.String> , bu kez iki parametreyle tanımlanır. İlk parametresi, `aString` Uzantı yönteminin genişlettiğini belirler <xref:System.String> . İkinci parametresi, `punc` yöntemi çağrıldığında bağımsız değişken olarak geçirilen bir noktalama işaretleri dizesi olmak üzere tasarlanmıştır. Yöntemi, dizeyi ve ardından noktalama işaretlerini görüntüler.

[!code-vb[VbVbalrExtensionMethods#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class2.vb#3)]

Yöntemi, için bir dize bağımsız değişkeninde göndererek çağrılır `punc` : `example.PrintAndPunctuate(".")`

Aşağıdaki örnek gösterir `Print` ve `PrintAndPunctuate` tanımlanır ve çağırılır. <xref:System.Runtime.CompilerServices> Uzantı özniteliğine erişimi etkinleştirmek için tanım modülüne içeri aktarılır.

```vb
Imports System.Runtime.CompilerServices

Module StringExtensions

    <Extension()>
    Public Sub Print(aString As String)
        Console.WriteLine(aString)
    End Sub

    <Extension()>
    Public Sub PrintAndPunctuate(aString As String, punc As String)
        Console.WriteLine(aString & punc)
    End Sub
End Module
```

Ardından, uzantı yöntemleri kapsama alınır ve çağrılır:

```vb
Imports ConsoleApplication2.StringExtensions

Module Module1

    Sub Main()
        Dim example As String = "Example string"
        example.Print()

        example = "Hello"
        example.PrintAndPunctuate(".")
        example.PrintAndPunctuate("!!!!")
    End Sub
End Module
```

Bu veya benzer uzantı yöntemlerini çalıştırmak için gerekli olan tüm bunlar kapsam içinde yer alırlar. Bir genişletme yöntemi içeren modül kapsamdadır, IntelliSense 'de görünür ve sıradan bir örnek yöntemi gibi çağrılabilir.

Yöntemler çağrıldığında, ilk parametre için ' de bir bağımsız değişken gönderildiğine dikkat edin. `aString`Önceki yöntem tanımlarındaki parametresi `example` , `String` bunları çağıran örneği olan öğesine bağlanır. Derleyici, `example` ilk parametreye gönderilen bağımsız değişken olarak kullanacaktır.

Olarak ayarlanmış bir nesne için bir genişletme yöntemi çağrılırsa `Nothing` , genişletme yöntemi yürütülür. Bu, sıradan örnek yöntemlerine uygulanmaz. Uzantı yönteminde açıkça kontrol edebilirsiniz `Nothing` .

## <a name="types-that-can-be-extended"></a>Genişletilebilen türler

Aşağıdakiler de dahil olmak üzere Visual Basic parametre listesinde gösterilebilen çoğu tür için bir genişletme yöntemi tanımlayabilirsiniz:

- Sınıflar (başvuru türleri)
- Yapılar (değer türleri)
- Arabirimler
- Temsilciler
- ByRef ve ByVal bağımsız değişkenleri
- Genel yöntem parametreleri
- Diziler

İlk parametre Uzantı yönteminin genişlettiği veri türünü belirttiğinden, gereklidir ve isteğe bağlı olamaz. Bu nedenle, `Optional` Parametreler ve `ParamArray` parametreleri parametre listesindeki ilk parametre olamaz.

Genişletme metotları geç bağlamada dikkate alınmıyor. Aşağıdaki örnekte, ifade `anObject.PrintMe()` bir <xref:System.MissingMemberException> özel durum oluşturur, ikinci `PrintMe` uzantı yöntemi tanımı silinmişse aynı özel durum görüntülenir.

[!code-vb[VbVbalrExtensionMethods#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class6.vb#9)]

## <a name="best-practices"></a>En iyi uygulamalar

Uzantı yöntemleri, var olan bir türü genişletmek için kullanışlı ve güçlü bir yol sağlar. Ancak, bunları başarılı bir şekilde kullanmak için göz önünde bulundurmanız gereken bazı noktaları vardır. Bu konular temel olarak sınıf kitaplıklarının yazarlarına uygulanır, ancak uzantı yöntemlerini kullanan herhangi bir uygulamayı etkileyebilir.

Genellikle, sahip olmadığınız türlere eklediğiniz genişletme yöntemleri, denetlediğiniz türlere eklenen genişletme yöntemlerinden daha savunmasız olacaktır. Uzantı yöntemlerinizi kesintiye uğratabilecek, sahip olmadığınız sınıflarda bir dizi şey meydana gelebilir.

- Çağırma deyimindeki bağımsız değişkenlerle uyumlu imzaya sahip herhangi bir erişilebilir örnek üye varsa, bağımsız değişkenden parametreye hiçbir daraltma dönüştürmesi gerekmiyorsa, örnek yöntemi herhangi bir genişletme yöntemine tercih edilir. Bu nedenle, belirli bir noktada bir sınıfa uygun bir örnek yöntemi eklenirse, kullandığınız mevcut bir uzantı üyesi erişilemez hale gelebilir.

- Bir genişletme yönteminin yazarı, diğer programcıların özgün uzantıya göre önceliğe sahip olabilecek, çakışan uzantı yöntemleri yazmasını engelleyemez.

- Uzantı yöntemlerini kendi ad alanına yerleştirerek sağlamlık düzeyini artırabilirsiniz. Daha sonra kitaplığınızın tüketicileri, bir ad alanı içerebilir veya hariç tutabilir ya da kitaplığın geri kalanından ayrı olarak ad alanları arasından seçim yapabilir.

- Arabirimleri genişletmekten daha güvenli olabilir, özellikle arabirimin veya sınıfınızın sahibi olmadığınız durumlarda sınıfları genişletebiliriz. Bir arabirimdeki değişiklik, onu uygulayan her sınıfı etkiler. Bu nedenle, yazarın bir arabirimdeki yöntemleri ekleme veya değiştirme olasılığı daha düşüktür. Ancak, bir sınıf aynı imzaya sahip uzantı yöntemlerine sahip iki arabirim uygularsa, hiçbir genişletme yöntemi görünür değildir.

- Kullanabileceğiniz en belirli türü genişletin. Bir tür hiyerarşisinde, diğer birçok türden türetilmiş bir tür seçerseniz, örnek yöntemlerinin veya sizinkilerle karıştabilecek diğer uzantı yöntemlerinin tanıtımı için bazı olanaklar katmanları vardır.

## <a name="extension-methods-instance-methods-and-properties"></a>Uzantı yöntemleri, örnek yöntemleri ve Özellikler

Kapsam içi bir örnek yöntemi, bir çağırma ifadesinin bağımsız değişkenleriyle uyumlu bir imzaya sahip olduğunda, örnek yöntemi herhangi bir genişletme yöntemine göre tercih edilir. Uzantı yöntemi daha iyi bir eşleşme olsa bile örnek yöntemi önceliğe sahiptir. Aşağıdaki örnekte, `ExampleClass` `ExampleMethod` türünde bir parametreye sahip adlı bir örnek yöntemi içerir `Integer` . Genişletme yöntemi `ExampleMethod` `ExampleClass` , ve türünde bir parametreye sahiptir `Long` .

[!code-vb[VbVbalrExtensionMethods#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class4.vb#4)]

Aşağıdaki kodda öğesine yapılan ilk çağrı `ExampleMethod` uzantı yöntemini çağırır, çünkü `arg1` `Long` ve yalnızca `Long` genişletme yöntemindeki parametresiyle uyumludur. İkinci çağrısının `ExampleMethod` bir `Integer` bağımsız değişkeni vardır `arg2` ve örnek yöntemini çağırır.

[!code-vb[VbVbalrExtensionMethods#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class4.vb#5)]

Şimdi iki yöntemde parametrelerin veri türlerini tersine çevirin:

[!code-vb[VbVbalrExtensionMethods#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class5.vb#6)]

Bu kez, içindeki kod `Main` her iki kez örnek yöntemini çağırır. Bunun nedeni, hem hem de `arg1` `arg2` üzerinde bir genişletme dönüştürmesi olması `Long` ve örnek yönteminin her iki durumda da genişletme yöntemine göre öncelikli olması olabilir.

[!code-vb[VbVbalrExtensionMethods#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class5.vb#7)]

Bu nedenle, bir genişletme yöntemi var olan bir örnek yönteminin yerini alamaz. Ancak, bir genişletme yöntemi bir örnek yöntemiyle aynı ada sahip olsa da imzalar çakışmadığında her iki yönteme de erişilebilir. Örneğin, sınıfı `ExampleClass` bağımsız değişken içermeyen adlı bir yöntemi içeriyorsa `ExampleMethod` , aşağıdaki kodda gösterildiği gibi, aynı ada sahip ve farklı imzalara sahip genişletme yöntemlerine izin verilir.

[!code-vb[VbVbalrExtensionMethods#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Module3.vb#8)]

Bu kodun çıktısı aşağıdaki gibidir:

```console
Extension method
Instance method
```

Durum, özelliklerle daha basittir: bir genişletme yöntemi, genişlettiği sınıfın bir özelliği ile aynı ada sahipse, genişletme yöntemi görünür değildir ve erişilemez.

## <a name="extension-method-precedence"></a>Uzantı yöntemi önceliği

Aynı imzaya sahip iki genişletme yöntemi kapsam içinde ve erişilebilir olduğunda, daha yüksek önceliğe sahip olan bir yöntem çağrılır. Uzantı yönteminin önceliği, yöntemi kapsama getirmek için kullanılan mekanizmaya dayanır. Aşağıdaki listede, en yüksekten en düşüğe öncelik hiyerarşisi gösterilmektedir.

1. Geçerli modülün içinde tanımlanan genişletme yöntemleri.

2. Geçerli ad alanındaki veya üst öğelerinden herhangi birindeki veri türleri içinde tanımlanan uzantı yöntemleri, alt ad alanları üst ad alanlarından daha yüksek önceliğe sahip.

3. Herhangi bir tür içinde tanımlanan genişletme yöntemleri geçerli dosyaya içe aktarılır.

4. Herhangi bir ad alanı içinde tanımlanan genişletme yöntemleri geçerli dosyaya içe aktarılır.

5. Herhangi bir proje düzeyi türü içeri aktarma içinde tanımlanan genişletme yöntemleri.

6. Herhangi bir proje düzeyi ad alanı içeri aktarma içinde tanımlanan genişletme yöntemleri.

Öncelik belirsizlik çözümlenmezse, aradığınız yöntemi belirtmek için tam nitelikli adı kullanabilirsiniz. `Print`Önceki örnekteki yöntem adlı bir modülde tanımlanmışsa `StringExtensions` , tam adı `StringExtensions.Print(example)` yerine olur `example.Print()` .

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.CompilerServices>
- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [Uzantı Metotları](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
- [Module Deyimi](../../../language-reference/statements/module-statement.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](procedure-parameters-and-arguments.md)
- [İsteğe Bağlı Parametreler](optional-parameters.md)
- [Parametre Dizileri](parameter-arrays.md)
- [Özniteliklere genel bakış](../../concepts/attributes/index.md)
- [Visual Basic'de Kapsam](../declared-elements/scope.md)
