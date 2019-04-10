---
title: Uzantı Yöntemleri (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ExtensionMethods
helpviewer_keywords:
- extending data types [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: b8020aae-374d-46a9-bcb7-8cc2390b93b6
ms.openlocfilehash: 9e005d0dc7da154fbaffbf7e02c55445a1213195
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59296244"
---
# <a name="extension-methods-visual-basic"></a>Uzantı Yöntemleri (Visual Basic)
Genişletme yöntemleri, geliştiricilerin zaten yeni bir türetilmiş tür oluşturmadan tanımlanan veri türlerine özel işlevsellik eklemek sağlar. Genişletme yöntemleri mevcut türü bir örnek yöntemi gibi çağrılabilen bir yöntem yazmaktır mümkün kılar.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir genişletme yöntemi yalnızca olabilir bir `Sub` yordamı veya `Function` yordamı. Bir uzantı özelliği, alan veya olay tanımlayamazsınız. Tüm uzantı yöntemleri uzantı özniteliğiyle işaretlenmelidir `<Extension()>` gelen <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> ad alanı.  
  
 Bir genişletme yöntemi tanımındaki ilk parametre, yöntemin genişlettiği hangi veri türünü belirtir. Yöntem çalıştırıldığında ilk parametre yöntemi çağıran veri türü örneğine bağlıdır.  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnekte tanımlayan bir `Print` uzantısı <xref:System.String> veri türü. Yöntemini kullanan `Console.WriteLine` bir dize görüntülemek için. Parametresi `Print` yöntemi `aString`, yöntem genişletir <xref:System.String> sınıfı.  
  
 [!code-vb[VbVbalrExtensionMethods#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/StringExtensions.vb#1)]  
  
 Uzantı yöntemi tanımının uzantı özniteliğiyle işaretlendiğine dikkat edin `<Extension()>`. Yöntemin tanımlandığı modülün işaretlenmesi isteğe bağlıdır, ancak her bir genişletme yöntemi işaretlenmelidir. <xref:System.Runtime.CompilerServices> Uzantı özniteliğine erişim sağlamak için içeri aktarılmalıdır.  
  
 Uzantı yöntemleri yalnızca modüllerde bildirilebilir. Genellikle, bir uzantı yönteminin tanımlandığı modül, çağrıldığı olarak aynı modül değil. Kapsama alınmak üzere olması gerekiyorsa bunun yerine, genişletme yöntemini içeren modül içe aktarılır. İçeren modül sonra `Print` olan yöntem kapsamda gibi hiçbir bağımsız değişken alan normal bir örnek yöntem gibi çağrılabilir `ToUpper`:  
  
 [!code-vb[VbVbalrExtensionMethods#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class1.vb#2)]  
  
 Sonraki örnek, `PrintAndPunctuate`, ayrıca bir uzantı olduğu <xref:System.String>, bu kez iki parametre ile tanımlanmıştır. İlk parametre `aString`, genişletme yönteminin genişletir <xref:System.String>. İkinci parametre `punc`, yöntem çağrıldığında, bağımsız değişken olarak geçirilen bir noktalama işaretleri dizesi olması amaçlanmıştır. Yöntem sonrasındaki noktalama işaretlerini görüntüler.  
  
 [!code-vb[VbVbalrExtensionMethods#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class2.vb#3)]  
  
 Yöntem için bir dize bağımsız değişken göndererek çağrılır `punc`: `example.PrintAndPunctuate(".")`  
  
 Aşağıdaki örnekte gösterildiği `Print` ve `PrintAndPunctuate` tanımlanan ve çağrılan. <xref:System.Runtime.CompilerServices> Uzantı özniteliğine erişim sağlamak için tanım modülüne içe aktarılır.  
  
### <a name="code"></a>Kod  
  
```vb  
Imports System.Runtime.CompilerServices  
  
Module StringExtensions  
  
    <Extension()>   
    Public Sub Print(ByVal aString As String)  
        Console.WriteLine(aString)  
    End Sub  
  
    <Extension()>   
    Public Sub PrintAndPunctuate(ByVal aString As String,   
                                 ByVal punc As String)  
        Console.WriteLine(aString & punc)  
    End Sub  
  
End Module  
```  
  
 Ardından, genişletme yöntemleri kapsama alınır ve çağrılır.  
  
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
  
### <a name="comments"></a>Açıklamalar  
 Tüm bunlar çalıştırılabilmesi için gereken veya benzer genişletme yöntemlerini kapsam içinde yer. Bir uzantı yöntemini içeren modül kapsamları dahilinde olması durumunda, Intellisense'te görünür duruma gelir ve normal bir örnek yöntem gibi çağrılabilir.  
  
 Yöntemler çağrıldığında hiçbir bağımsız değişken ilk parametre için gönderilmediğine dikkat edin. Parametre `aString` önceki yöntem tanımlarını bağlı `example`, örneğini `String` onları çağırır. Derleyicinin kullanacağı `example` ilk parametreye gönderilen bağımsız değişken olarak.  
  
 Ayarlanmış bir nesne için bir genişletme yöntemi çağrılırsa `Nothing`, genişletme yöntemi yürütülür. Bu sıradan örnek yöntemleri için geçerli değildir. Açıkça denetleyebilirsiniz `Nothing` uzantı yönteminde.  
  
## <a name="types-that-can-be-extended"></a>Genişletilebilen türler  
 Aşağıdakiler dahil olmak üzere bir Visual Basic parametre listesinde temsil edilebilir çoğu türlerinde bir genişletme yöntemi tanımlayabilirsiniz:  
  
-   Sınıflar (başvuru türleri)  
  
-   Yapılar (değer türleri)  
  
-   Arabirimler  
  
-   Temsilciler  
  
-   ByRef ve ByVal bağımsız değişkenleri  
  
-   Genel yöntem parametreleri  
  
-   Diziler  
  
 İlk parametre genişletme yönteminin genişlettiği veri türünü belirttiğinden gereklidir ve isteğe bağlı olamaz. Bu nedenle `Optional` parametreleri ve `ParamArray` parametreleri parametre listesindeki ilk parametre olamaz.  
  
 Genişletme yöntemleri geç bağlama kapsamında değerlendirilmez. Aşağıdaki örnekte, deyim `anObject.PrintMe()` başlatan bir <xref:System.MissingMemberException> özel durum, görüyorsanız, aynı özel durum ikinci `PrintMe` genişletme yöntemi tanımı silindiğinde.  
  
 [!code-vb[VbVbalrExtensionMethods#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class6.vb#9)]  
  
## <a name="best-practices"></a>En İyi Yöntemler  
 Genişletme yöntemleri mevcut türü genişletmek için kullanışlı ve güçlü bir yol sağlar. Ancak, başarıyla kullanmak için dikkate alınması gereken bazı noktalar vardır. Esas olarak sınıf kitaplıklarını yazarları için aşağıdaki maddeler geçerlidir, ancak bunlar genişletme yöntemlerini kullanan tüm uygulamaları etkileyebilir.  
  
 Genellikle sahibi olmadığınız türlere eklediğiniz genişletme yöntemleri daha denetim türlere eklenen genişletme yöntemlerinden daha savunmasızdır. Birkaç uzantı yöntemlerinizi engelleyebilecek birçok ait olmayan sınıflarda ortaya çıkabilir.  
  
-   Parametreye daraltma dönüşümü bağımsız değişkenden parametreye ile çağrı deyimindeki bağımsız değişkenlerle uyumlu imzası olan bir erişilebilir örnek üye varsa, örnek yöntemi herhangi bir genişletme yöntemi yerine kullanılacaktır. Bu nedenle, uygun bir örnek yöntemi, belirli bir noktada bir sınıfa eklenirse, bağlı olduğunuz mevcut uzantı üyesi erişilemez duruma gelebilir.  
  
-   Genişletme yönteminin yazarı diğer programcıların öncelik özgün öncelikli olabilecek, çakışan genişletme yöntemleri yazmasını engelleyemez.  
  
-   Genişletme yöntemleri kendi ad alanına yerleştirerek sağlamlığı artırabilirsiniz. Kitaplığınızı kullanan Tüketiciler, bir ad alanı dahil edebilir veya hariç veya kitaplık kalanından ayrı olarak ad alanları arasından seçim.  
  
-   Özellikle, arabirimin veya sınıfın sahibi değil, bu sınıfları genişletmek yerine arabirimleri genişletmek daha güvenli olabilir. Arabirimdeki bir değişiklik, uygulandığı her sınıfı etkiler. Bu nedenle, yazarın ekleme veya bir arabirimdeki yöntemlerde değiştirme olasılığı daha az olabilir. Ancak, bir sınıf, aynı imzaya sahip genişletme yöntemleri olan iki arabirim uygularsa, her iki uzantı yöntemi görülebilir.  
  
-   Yapabilecekleriniz en belirgin türü genişletin. Tür hiyerarşisinde çok türetildiği bir tür seçerseniz katmanı vardır örnek yöntemlerine veya yöntemlerinizle çakışabilecek genişletme yöntemlerine giriş olasılıklarını.  
  
## <a name="extension-methods-instance-methods-and-properties"></a>Genişletme yöntemleri, örnek yöntemler ve Özellikler  
 Bir kapsamdaki örnek yöntemi deyim çağırma bağımsız değişkenlerle uyumlu imzası olan, örnek yöntemi yerine herhangi bir genişletme yöntemi seçilir. Genişletme yönteminin eşleşmesi daha iyi olsa bile örnek yönteminindir. Aşağıdaki örnekte, `ExampleClass` adlandırılmış bir örnek yöntemi içeren `ExampleMethod` türünde bir parametreye sahip `Integer`. Genişletme yöntemi `ExampleMethod` genişletir `ExampleClass`, ve türünde bir parametreye sahip `Long`.  
  
 [!code-vb[VbVbalrExtensionMethods#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class4.vb#4)]  
  
 İlk çağrıda `ExampleMethod` aşağıdaki kodda genişletme yöntemini çağırır çünkü `arg1` olduğu `Long` ve yalnızca ile uyumlu `Long` genişletme yönteminin parametresi. İçin yapılan ikinci çağrı `ExampleMethod` sahip bir `Integer` bağımsız değişkeni, `arg2`, ve örnek yöntemini çağırır.  
  
 [!code-vb[VbVbalrExtensionMethods#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class4.vb#5)]  
  
 Şimdi geriye doğru iki yöntemle parametrelerinin veri türleri:  
  
 [!code-vb[VbVbalrExtensionMethods#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class5.vb#6)]  
  
 Bu sefer kodda `Main` iki seferde de örnek yöntemini çağırır. Bunun nedeni, her ikisi de `arg1` ve `arg2` genişletme dönüştürmesi sahip `Long`, ve örnek yöntemin her iki durumda da uzantı yöntemini önceliklidir.  
  
 [!code-vb[VbVbalrExtensionMethods#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class5.vb#7)]  
  
 Bu nedenle, bir genişletme yöntemi, bir mevcut örnek yönteminin yerine kullanılamaz. Ancak, bir genişletme yöntemi örnek yöntemle aynı ada sahiptir ancak imzalar, her iki yöntem de erişilebilir. Örneğin, sınıf `ExampleClass` adında bir yöntem içeriyorsa `ExampleMethod` hiçbir bağımsız değişken, aynı ada sahip genişletme yöntemleri alır ancak farklı imzalara izin verilir, aşağıdaki kodda gösterildiği gibi.  
  
 [!code-vb[VbVbalrExtensionMethods#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Module3.vb#8)]  
  
 Bu kodun çıktısı aşağıdaki gibidir:  
  
 `Extension method`  
  
 `Instance method`  
  
 Durum özellikler ile daha basittir: genişletme yöntemi genişlettiği sınıfın bir özelliği aynı ada sahipse, genişletme yöntemi görünmez ve erişilemez.  
  
## <a name="extension-method-precedence"></a>Genişletme yöntemini önceliği  
 Aynı imzaya sahip iki uzantı yöntemi kapsam içinde ve erişilebilir olduğunda, daha yüksek önceliğe sahip çağrılır. Bir uzantı yönteminin önceliği, yöntemi kapsam içine almak için kullanılan mekanizmaya dayanır. Aşağıdaki liste, yüksekten en düşüğe öncelik hiyerarşisini gösterir.  
  
1. Geçerli modül içinde tanımlanan genişletme yöntemleri.  
  
2. Genişletme yöntemleri veri türleri geçerli ad alanı veya üst öğelerinden birini üst öğe ad alanlarına daha yüksek bir önceliğe sahip alt ad alanları ile tanımlanır.  
  
3. Geçerli dosyadaki herhangi bir türü alır içinde tanımlanan genişletme yöntemleri.  
  
4. Geçerli dosyadaki tüm ad alanı içeri aktarmaları içinde tanımlanan genişletme yöntemleri.  
  
5. Tüm proje düzeyi türündeki aktarılır tanımlanan genişletme yöntemleri.  
  
6. Tüm proje düzeyindeki ad alanında aktarılır tanımlanan genişletme yöntemleri.  
  
 Öncelik belirsizliği, kaldırmazsa çağırdığınız yöntemi belirtmek için tam nitelikli adı kullanabilirsiniz. Varsa `Print` yöntemi önceki örnekte bulunan adında bir modülde tanımlanan `StringExtensions`, tam nitelikli ad `StringExtensions.Print(example)` yerine `example.Print()`.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.CompilerServices>
- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [Genişletme Yöntemleri](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
- [Module Deyimi](../../../../visual-basic/language-reference/statements/module-statement.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [İsteğe Bağlı Parametreler](./optional-parameters.md)
- [Parametre Dizileri](./parameter-arrays.md)
- [Öznitelikler genel bakış](../../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [Visual Basic'de Kapsam](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
