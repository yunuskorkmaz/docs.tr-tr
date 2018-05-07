---
title: Uzantı Metotları (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ExtensionMethods
helpviewer_keywords:
- extending data types [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: b8020aae-374d-46a9-bcb7-8cc2390b93b6
ms.openlocfilehash: 1cc2ccef09dd027c6f1e82f60ed4ac5f50db6ebe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="extension-methods-visual-basic"></a>Uzantı Metotları (Visual Basic)
Genişletme yöntemleri yeni türetilmiş bir tür oluşturmadan önceden tanımlanmış veri türlerine özel işlevsellik eklemek için geliştiricilere etkinleştirin. Genişletme yöntemleri varolan türünün bir örneği yöntemi değilmiş gibi çağrılabilir bir yöntem yazmak mümkün kılar.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir genişletme yöntemi yalnızca olabilir bir `Sub` yordamı veya `Function` yordamı. Uzantı özelliği, alan veya olay tanımlayamazsınız. Tüm uzantı yöntemleri uzantısı özniteliği ile işaretlenmiş olmalıdır `<Extension()>` gelen <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> ad alanı.  
  
 Bir genişletme yöntemi tanımında ilk parametresi, yöntemin genişlettiği hangi veri türünü belirtir. Yöntem çalıştırdığınızda, ilk parametre yöntemi çağırır veri türü örneğine bağlı.  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek tanımlayan bir `Print` uzantısı <xref:System.String> veri türü. Bir yöntem `Console.WriteLine` bir dize görüntülemek için. Parametresi, `Print` yöntemi, `aString`, yöntemin genişlettiği kurar <xref:System.String> sınıfı.  
  
 [!code-vb[VbVbalrExtensionMethods#1](./codesnippet/VisualBasic/extension-methods_1.vb)]  
  
 Uzantı yöntemi tanımı uzantısı özniteliğiyle işaretlenmiş fark `<Extension()>`. Yöntem tanımlandığı modülü işaretleme isteğe bağlıdır, ancak her bir genişletme yöntemi işaretlenmesi gerekir. <xref:System.Runtime.CompilerServices> Uzantı özniteliği erişmek için içeri aktarılmalıdır.  
  
 Genişletme yöntemleri yalnızca modülleri içinde bildirilebilir. Genellikle, bir genişletme yöntemi tanımlandığı modül adı verilir olarak aynı modül değil. Bu kapsam içine duruma getirmek üzere olması gerekiyorsa bunun yerine, genişletme yöntemi içeren modülü, içeri aktarılır. İçeren modülü sonra `Print` olduğu gibi hiç bağımsız değişken alan sıradan örnek yöntemi değilmiş gibi kapsamda yöntemi çağrılabilir `ToUpper`:  
  
 [!code-vb[VbVbalrExtensionMethods#2](./codesnippet/VisualBasic/extension-methods_2.vb)]  
  
 Sonraki örnek `PrintAndPunctuate`, ayrıca bir uzantı olduğu <xref:System.String>, iki parametreyle tanımlanan bu süre. İlk parametre `aString`, genişletme yöntemi genişleten kurar <xref:System.String>. İkinci parametre `punc`, yöntem çağrıldığında, bağımsız değişken olarak geçirilen noktalama işaretleri dizesi olması amaçlanmıştır. Yöntem noktalama işaretleri tarafından izlenen dizesi görüntüler.  
  
 [!code-vb[VbVbalrExtensionMethods#3](./codesnippet/VisualBasic/extension-methods_3.vb)]  
  
 Dize bağımsız değişkeni için göndererek çağrılan yöntemi `punc`: `example.PrintAndPunctuate(".")`  
  
 Aşağıdaki örnekte gösterildiği `Print` ve `PrintAndPunctuate` tanımlanan ve çağrılır. <xref:System.Runtime.CompilerServices> tanımı modülünde extension özniteliği erişimi etkinleştirmek için alınır.  
  
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
  
 Ardından, genişletme yöntemleri kapsam içine alınır ve çağrılır.  
  
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
 Tüm bunlar çalıştırılabilmesi için gereken veya benzer genişletme yöntemleri kapsamında olmalıdır. Bir genişletme yöntemi içeren modülü kapsamları dahilinde olması durumunda, IntelliSense içinde görünür ve sıradan örnek yöntemi değilmiş gibi çağrılabilir.  
  
 Yöntem çağrıldığında, bağımsız değişken ilk parametre için gönderilmesini dikkat edin. Parametre `aString` önceki yönteminde tanımları bağlı `example`, örneği `String` bunları çağırır. Derleyici kullanacağı `example` ilk parametre olarak gönderilen bağımsız değişken olarak.  
  
 Ayarlanmış bir nesne için bir genişletme yöntemi çağrılıp çağrılmayacağını `Nothing`, genişletme yöntemi yürütür. Bu normal örnek yöntemleri için geçerli değildir. Açıkça denetleyebilirsiniz `Nothing` uzantı yönteminde.  
  
## <a name="types-that-can-be-extended"></a>Genişletilebilir türleri  
 Bir genişletme yöntemi, aşağıdakiler de dahil olmak üzere bir Visual Basic parametre listesinde, temsil edilebilir çoğu türlerinde tanımlayabilirsiniz:  
  
-   Sınıflar (başvuru türleri)  
  
-   Yapılar (değer türleri için)  
  
-   Arabirimler  
  
-   Temsilciler  
  
-   ByRef ve ByVal bağımsız değişkenler  
  
-   Genel yöntem parametreleri  
  
-   Diziler  
  
 İlk parametre uzantısı yöntemin genişlettiği veri türü belirttiğinden, gerekli ve isteğe bağlı olamaz. Bu nedenle, `Optional` parametreleri ve `ParamArray` parametreleri, parametre listesindeki ilk parametre olamaz.  
  
 Genişletme yöntemleri geç bağlama dikkate alınmaz. Aşağıdaki örnekte, deyim `anObject.PrintMe()` başlatır bir <xref:System.MissingMemberException> özel durum, görüyorsanız, aynı özel durum ikinci `PrintMe` yöntemi tanımı uzantısı silindi.  
  
 [!code-vb[VbVbalrExtensionMethods#9](./codesnippet/VisualBasic/extension-methods_4.vb)]  
  
## <a name="best-practices"></a>En İyi Yöntemler  
 Genişletme yöntemleri, mevcut bir türle genişletmek için kullanışlı ve güçlü bir yol sağlar. Ancak, başarılı bir şekilde kullanmak için vardır bazı noktaları göz önünde bulundurun. Bu noktalar çoğunlukla sınıf kitaplıkları yazarları için geçerlidir, ancak genişletme yöntemlerini kullanan herhangi bir uygulama etkileyebilir.  
  
 En genel olarak, sahibi olmadığınız türleri ekleme genişletme yöntemleri, sizin denetlediğiniz türlerine eklenen genişletme yöntemleri daha savunmasız. Birkaç uzantı yöntemleriyle etkileyebilir sahibi olmadığınız sınıflardaki ortaya çıkabilir.  
  
-   Bağımsız değişkenden parametresi gerekli hiçbir daraltma dönüşümleri ile arama deyiminde bağımsız değişkenle uyumlu bir imzaya sahip herhangi bir erişilebilir örneği üyesi varsa, örnek yöntemi herhangi bir genişletme yöntemi yerine kullanılır. Bu nedenle, uygun örnek yöntemi, belirli bir noktada bir sınıfa eklediyseniz, bağlı olan bir uzantı üye erişilemez hale gelebilir.  
  
-   Bir genişletme yöntemi yazarı diğer programcıları öncelik özgün uzantısı olabilir çakışan genişletme yöntemleri yazma engelleyemez.  
  
-   Genişletme yöntemleri, kendi ad alanında koyarak sağlamlık artırabilir. Tüketiciler kitaplığınızın bir ad alanı dahil edebilir veya dışarıda veya ad alanları, ayrı ayrı geri kalanından kitaplığı arasından seçim.  
  
-   Özellikle, arabirimi veya sınıfı değil sahipseniz sınıfları, genişletilecek olduğundan arabirimleri genişletmek daha güvenli olabilir. Arabirimdeki bir değişiklik, uygulayan her sınıf etkiler. Bu nedenle, yazarın eklemek veya bir arabirim yöntemleri değiştirmek olasılığı daha düşüktür. Ancak, bir sınıf uzantısı yöntemleri aynı imzayla iki arabirim uygularsa, hiçbiri genişletme yöntemi görünür olur.  
  
-   Yapabilecekleriniz en belirgin türü genişletir. Türlerinin bir hiyerarşide, diğer birçok türetilen, bir tür seçerseniz katmanı vardır olasılıklar giriş örnek yöntemleri ya da sizin ile engelleyebilmesi diğer genişletme yöntemleri.  
  
## <a name="extension-methods-instance-methods-and-properties"></a>Genişletme yöntemleri, örnek yöntemleri ve özellikleri  
 Kapsam örnek yöntemi çağıran bir deyim bağımsız değişkenleri ile uyumlu bir imzası olduğunda, örnek yöntemi yerine herhangi bir genişletme yöntemi seçilir. Daha iyi bir eşleşme genişletme yöntemi olsa bile, örnek yöntemi önceliğe sahiptir. Aşağıdaki örnekte, `ExampleClass` adlandırılmış bir örnek yöntemi içerir `ExampleMethod` türünde bir parametre olan `Integer`. Genişletme yöntemi `ExampleMethod` genişletir `ExampleClass`, ve parametresinin türü `Long`.  
  
 [!code-vb[VbVbalrExtensionMethods#4](./codesnippet/VisualBasic/extension-methods_5.vb)]  
  
 İlk çağrıda `ExampleMethod` aşağıdaki kodda genişletme yöntemi çağırır çünkü `arg1` olan `Long` ve yalnızca ile uyumlu `Long` genişletme yöntemi parametresinde. İkinci çağrı `ExampleMethod` sahip bir `Integer` bağımsız değişkeni, `arg2`, ve örnek yöntemini çağırır.  
  
 [!code-vb[VbVbalrExtensionMethods#5](./codesnippet/VisualBasic/extension-methods_6.vb)]  
  
 Şimdi geriye doğru parametrelere iki yöntem de veri türleri:  
  
 [!code-vb[VbVbalrExtensionMethods#6](./codesnippet/VisualBasic/extension-methods_7.vb)]  
  
 Bu sefer kodda `Main` iki kez örneği yöntemini çağırır. Bunun nedeni, her ikisi de `arg1` ve `arg2` değerine Genişletme dönüşümü `Long`, ve örnek yöntemi her iki durumda da genişletme yöntemi önceliklidir.  
  
 [!code-vb[VbVbalrExtensionMethods#7](./codesnippet/VisualBasic/extension-methods_8.vb)]  
  
 Bu nedenle, bir genişletme yöntemi, varolan bir örnek yöntemi değiştirilemiyor. Ancak, bir genişletme yöntemi örnek yöntemi olarak aynı ada sahip ancak imzaları çakışmasını yöntemlerin her ikisi de erişilebilir. Örneğin, varsa sınıfı `ExampleClass` adlı bir yöntem içerir `ExampleMethod` hiçbir bağımsız değişkenler, aynı ada sahip genişletme yöntemleri alır ancak farklı imzalar izin verilir, aşağıdaki kodda gösterildiği gibi.  
  
 [!code-vb[VbVbalrExtensionMethods#8](./codesnippet/VisualBasic/extension-methods_9.vb)]  
  
 Bu kod çıkışı aşağıdaki gibidir:  
  
 `Extension method`  
  
 `Instance method`  
  
 Durum özelliklerle basittir: bir genişletme yöntemi, genişletir sınıfın özelliği aynı ada sahipse, genişletme yöntemi görünür değil ve erişilemiyor.  
  
## <a name="extension-method-precedence"></a>Uzantı yöntemi önceliği  
 Daha yüksek önceliğe sahip olanla aynı imzaya sahip iki uzantı yöntemleri kapsamında ve erişilebilir olduğunda çağrılır. Bir uzantı yöntemin öncelik yöntemi kapsam içine getirmek için kullanılan mekanizmasını temel alır. Aşağıdaki listede yüksekten en düşüğe öncelik hiyerarşisini gösterir.  
  
1.  İçinde bulunduğu geçerli modülü tanımlanan genişletme yöntemleri.  
  
2.  Genişletme yöntemleri içinde veri türleri geçerli ad veya üst öğelerinden birini üst ad alanları daha yüksek önceliğe sahip alt ad ile tanımlanır.  
  
3.  Geçerli dosyasında bulunan tüm türü içeri aktarmalar içinde tanımlanan genişletme yöntemleri.  
  
4.  Tüm ad alanı içe aktarımlarını geçerli dosyasında içinde tanımlanan genişletme yöntemleri.  
  
5.  Tüm proje düzeyi türü içeri aktarmalar içinde tanımlanan genişletme yöntemleri.  
  
6.  Tüm proje düzeyi ad alanı içeri aktarmalar içinde tanımlanan genişletme yöntemleri.  
  
 Öncelik belirsizliği çözmezse tam adı, aradığınız yöntemini belirtmek için kullanabilirsiniz. Varsa `Print` yöntemi önceki örnekte adlı bir modülde tanımlanan `StringExtensions`, tam ad `StringExtensions.Print(example)` yerine `example.Print()`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.CompilerServices>  
 <xref:System.Runtime.CompilerServices.ExtensionAttribute>  
 [Genişletme Yöntemleri](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)  
 [Module Deyimi](../../../../visual-basic/language-reference/statements/module-statement.md)  
 [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)  
 [İsteğe Bağlı Parametreler](./optional-parameters.md)  
 [Parametre Dizileri](./parameter-arrays.md)  
 [Öznitelikler genel bakış](../../../../visual-basic/programming-guide/concepts/attributes/index.md)  
 [Visual Basic'de kapsam](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
