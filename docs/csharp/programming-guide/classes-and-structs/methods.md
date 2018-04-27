---
title: Yöntemler (C# Programlama Kılavuzu)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- methods [C#]
- C# language, methods
ms.assetid: cc738f07-e8cd-4683-9585-9f40c0667c37
caps.latest.revision: 41
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: dad1be88e39b708d34f454875e2cfb3ec100c430
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="methods-c-programming-guide"></a>Yöntemler (C# Programlama Kılavuzu)
Bir dizi deyimi içeren kod bloğu bir yöntemdir. Bir program yöntemini çağırarak ve tüm gerekli yöntemi bağımsız değişkenleri belirtme yürütülecek deyimleri neden olur. C# ' ta yürütülen her yönerge bir yöntem bağlamında gerçekleştirilir. Main yöntemi her C# uygulaması için giriş noktasıdır ve program başlatıldığında, ortak dil çalışma zamanı tarafından (CLR) adı verilir.  
  
> [!NOTE]
>  Bu konu, adlandırılmış yöntemleri açıklar. Anonim işlevler hakkında daha fazla bilgi için bkz: [anonim işlevler](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).  
  
## <a name="method-signatures"></a>Yöntem imzaları  
 İçinde bildirilen yöntemleri bir [sınıfı](../../../csharp/language-reference/keywords/class.md) veya [yapısı](../../../csharp/language-reference/keywords/struct.md) erişim düzeyini gibi belirterek `public` veya `private`, isteğe bağlı değiştiricileri gibi `abstract` veya `sealed`, dönüş değer, yöntemi ve herhangi bir yöntem parametre adı. Bu bölümleri yöntemi imzası birleştirilir.  
  
> [!NOTE]
>  Bir yöntemin dönüş türü yöntemi için yöntem aşırı yükleme amacıyla imza parçası değil. Ancak, bir temsilci ve işaret yöntemi uyumluluğu belirlerken yöntemi imzası parçası olan.  
  
 Yöntem parametreleri parantez içine alınmış ve virgülle ayrılır. Boş parantez yöntemi hiçbir parametre gerektirmiyor gösterir. Bu sınıf, üç yöntem içerir:  
  
 [!code-csharp[csProgGuideObjects#40](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_1.cs)]  
  
## <a name="method-access"></a>Yöntem erişimi  
 Bir nesne üzerinde bir yöntemi çağırmak için bir alan erişim gibi olur. Nesne adından sonra bir süre, yöntemi ve parantez adını ekleyin. Bağımsız değişkenler ayraç içinde listelenmiştir ve virgülle ayrılır. Yöntemlerinin `Motorcycle` sınıfı bu nedenle aşağıdaki örnekteki çağrılabilir:  
  
 [!code-csharp[csProgGuideObjects#41](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_2.cs)]  
  
## <a name="method-parameters-vs-arguments"></a>Yöntem parametreleri vs. Arguments  
 Yöntem tanımı adlarını ve gerekli olan herhangi bir parametre türlerini belirtir. Kod çağrıları yöntemi çağrılırken, her parametre için bağımsız değişken olarak adlandırılan somut değerleri sağlar. Bağımsız değişken parametre türü ile uyumlu olması gerekir, ancak çağıran kod içinde kullanılan bağımsız değişken adı (varsa) aynı adlı parametre yönteminde tanımlanmış olması gerekmez. Örneğin:  
  
 [!code-csharp[csProgGuideObjects#74](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_3.cs)]  
  
## <a name="passing-by-reference-vs-passing-by-value"></a>Başvuru vs geçirerek. Değere göre geçirme  
 Varsayılan olarak, bir değer türü bir yönteme geçirildiğinde nesne yerine bir kopyasını geçirilir. Bu nedenle, bağımsız değişkenin değişiklikleri arama yönteminde özgün kopya üzerinde etkisi yoktur. Ref anahtar sözcüğünü kullanarak bir değer türü başvurusu tarafından geçirebilirsiniz. Daha fazla bilgi için bkz: [değer türü parametrelerini geçirme](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md). Yerleşik değer türlerinin listesi için bkz: [değer türleri tablosu](../../../csharp/language-reference/keywords/value-types-table.md).  
  
 Nesneye bir başvurusu, başvuru türünde bir nesne için bir yöntem geçirildiğinde geçirilir. Diğer bir deyişle, nesnenin kendisini değil ancak nesnenin konumunu belirten bir bağımsız değişken yöntemi alır. Bu başvuru kullanarak nesne üyesi değiştirirseniz, değeri tarafından nesneyi geçirin olsa bile değişiklik arama yönteminde bağımsız yansıtılır.  
  
 Kullanarak bir başvuru türü oluşturma `class` aşağıdaki örnekte gösterildiği gibi anahtar sözcüğü.  
  
 [!code-csharp[csProgGuideObjects#42](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_4.cs)]  
  
 Şimdi, bu tür bir yönteme dayalı bir nesne geçirirseniz, nesneye bir başvurusu geçirilir. Aşağıdaki örnekte bir nesne türü geçirir `SampleRefType` yöntemine `ModifyObject`.  
  
 [!code-csharp[csProgGuideObjects#75](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_5.cs)]  
  
 Bu bağımsız değişken değeri tarafından bir yönteme geçirir, örneğin önceki örnekte temelde aynı şeyi yapar. Ancak, bir başvuru türü kullanıldığından, sonuç farklıdır. İçinde yapılan değişiklik `ModifyObject` için `value` parametre alan `obj`, ayrıca değiştirir `value` bağımsız değişken alan `rt`, `TestRefType` yöntemi. `TestRefType` Yöntemi 33 çıkış olarak görüntüler.  
  
 Başvuru türleri başvuruya göre ve değerine göre geçirmek hakkında daha fazla bilgi için bkz: [başvuru türü parametreleri geçirme](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md) ve [başvuru türleri](../../../csharp/language-reference/keywords/reference-types.md).  
  
## <a name="return-values"></a>Dönüş Değerleri  
Yöntemleri bir değer çağırana geri dönebilirsiniz. Dönüş türü, yöntem adı önce listelenen türü değil `void`, yöntem kullanarak değeri döndürebilir `return` anahtar sözcüğü. With deyimi `return` anahtar sözcüğünü dönüş türüyle eşleşen bir değeri tarafından yöntemi çağırana bu değeri döndürür. 

Değeri veya, C# 7.0 ile başlayan çağırana döndürülebilecek değeri [başvuruya göre](ref-returns.md). Değerleri çağırana döndürülen başvuruya göre `ref` anahtar sözcüğü yöntemi imzada kullanılır ve her izleyen `return` anahtar sözcüğü. Örneğin, aşağıdaki yöntemi imza ve return deyimi belirtmek yöntemi bir değişken adlarını döndürür `estDistance` çağırana başvuruya.

```csharp
public ref double GetEstimatedDistance()
{
   return ref estDistance;
}
```

`return` Anahtar sözcüğü yönteminin yürütülmesi de durdurulur. Dönüş türü ise `void`, `return` deyimi bir değer olmadan yönteminin yürütülmesi durdurmak hala faydalıdır. Olmadan `return` anahtar sözcüğü yöntemi durduracak kod bloğunu sonuna ulaştığında yürütülüyor. Void olmayan yöntemleriyle dönüş türü kullanmak için gerekli `return` bir değer döndürmek üzere anahtar sözcük. Örneğin, bu iki yöntem kullanmak `return` tamsayılar döndürmek için anahtar sözcüğü:  
  
 [!code-csharp[csProgGuideObjects#44](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_6.cs)]  
  
 Bir yönteminden döndürülen bir değer kullanmak için arama yöntemi aynı türde bir değer yeterli olacaktır yöntem çağrısının kendisini her yerde kullanabilirsiniz. Dönüş değeri bir değişkene de atayabilirsiniz. Örneğin, aşağıdaki iki kod örnekleri aynı hedefe gerçekleştirirsiniz:  
  
 [!code-csharp[csProgGuideObjects#45](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_7.cs)]  
  
 [!code-csharp[csProgGuideObjects#46](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_8.cs)]  
  
 Yerel bir değişken, bu durumda, kullanarak `result`depolamak için bir değer isteğe bağlıdır. Tüm kapsamını yöntemi için bağımsız değişken özgün değeri depolamak gerekiyorsa gerekli olabilir veya kod okunabilirliğini yardımcı olabilir.  

Bir yöntem başvurusundan tarafından döndürülen bir değer kullanmak için bildirmelisiniz bir [ref yerel](ref-returns.md#ref-locals) değerini değiştirmek istiyorsanız, değişkeni. Örneğin, varsa `Planet.GetEstimatedDistance` yöntemi döndürür bir <xref:System.Double> değeri başvuruya göre bunu aşağıdaki gibi bir kodla ref yerel değişken olarak tanımlayabilirsiniz:

```csharp
ref int distance = plant 
```

Bir yöntemi, çok boyutlu bir dizi döndürme `M`, dizinin değiştiren içeriği çağıran işlevi diziye aktarılırsa gerekli olmadığı `M`.  Sonuçta elde edilen diziden döndürebilir `M` iyi stili veya değerleri, ancak işlev akışını çünkü C# değerine göre tüm başvuru türleri geçirir ve bir dizi başvurusu dizi yönelik işaretçinin değeri gerekli değildir. Yönteminde `M`, aşağıdaki örnekte gösterildiği gibi dizinin içeriğini herhangi bir değişiklik observable dizi başvuruyor herhangi bir kod tarafından şunlardır.  
  
```csharp  
static void Main(string[] args)  
        {  
            int[,] matrix = new int[2, 2];  
            FillMatrix(matrix);  
            // matrix is now full of -1  
        }  
  
        public static void FillMatrix(int[,] matrix)  
        {  
            for (int i = 0; i < matrix.GetLength(0); i++)  
            {  
                for (int j = 0; j < matrix.GetLength(1); j++)  
                {  
                    matrix[i, j] = -1;  
                }  
            }  
        }  
```  
  
 Daha fazla bilgi için bkz: [iade](../../../csharp/language-reference/keywords/return.md).  
  
## <a name="async-methods"></a>Zaman uyumsuz yöntemleri  
 Async özelliği kullanarak, açık geri aramalar kullanarak veya birden çok yöntem veya lambda ifadeleri kodunuzu el ile bölme olmadan zaman uyumsuz yöntemleri çağırabilirsiniz. 
  
 Bir yöntem ile işaretlerseniz [zaman uyumsuz](../../../csharp/language-reference/keywords/async.md) kullanabileceğiniz değiştiricisi, [await](../../../csharp/language-reference/keywords/await.md) yönteminde işleci. Denetim async yöntemi bekleme deyimde ulaştığında çağırana denetimini döndürür ve yöntemi ediyor awaited görevi tamamlanana kadar bekletilir. Görev tamamlandığında, yürütme yönteminde devam edebilirsiniz.  
  
> [!NOTE]
>  Bir zaman uyumsuz yöntem henüz tamamlanmadı ilk awaited nesne bulduğu veya zaman uyumsuz yönteminin sonuna alır çağırana döndürür hangisi önce gerçekleşir.  
  
 Zaman uyumsuz yöntem dönüş türüne sahip olabilir <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>, ya da geçersiz. Dönüş türü void dönüş türü void gerekli olduğu öncelikle olay işleyicileri tanımlamak için kullanılır. Void döndüren bir zaman uyumsuz yöntem beklemenin ve void döndüren bir yöntem arayan yöntemi atar özel durumlarını yakalama olamaz.  
  
 Aşağıdaki örnekte, `DelayAsync` dönüş türüne sahip bir zaman uyumsuz yöntem <xref:System.Threading.Tasks.Task%601>. `DelayAsync` sahip bir `return` deyimi bir tamsayı döndürür. Bu nedenle yöntemi bildirimi `DelayAsync` dönüş türüne sahip olmalıdır `Task<int>`. Dönüş türü olduğundan `Task<int>`, değerlendirmesi `await` ifadesinde `DoSomethingAsync` aşağıdaki ifadeyi gösterdiği gibi bir tamsayı üretir: `int result = await delayTask`.  
  
 `startButton_Click` Yöntemi geçersiz dönüş türüne sahip bir zaman uyumsuz yöntem örneğidir. Çünkü `DoSomethingAsync` bir zaman uyumsuz yöntem çağrısı için görev `DoSomethingAsync` , aşağıdaki deyimi gösterildiği beklemenin gerekir: `await DoSomethingAsync();`. `startButton_Click` Yöntemi ile tanımlanması gerekir `async` değiştirici yöntem sahip olduğu bir `await` ifade.  
  
 [!code-csharp[csAsyncMethod#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_9.cs)]  
  
 Herhangi bir zaman uyumsuz yöntem bildiremezsiniz [ref](../../../csharp/language-reference/keywords/ref.md) veya [çıkışı](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametreleri, ancak bu tür parametrelerine sahip yöntemleri çağırabilirsiniz.  
  
 Zaman uyumsuz yöntemleri hakkında daha fazla bilgi için bkz [zaman uyumsuz programlama ile async ve await](../../../csharp/programming-guide/concepts/async/index.md), [akış denetimi zaman uyumsuz programlarda](../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md), ve [zaman uyumsuz dönüş türleri](../../../csharp/programming-guide/concepts/async/async-return-types.md).  
  
## <a name="expression-body-definitions"></a>İfade gövdesi tanımları  
 Yalnızca hemen ifade ile sonuç ya da tek bir deyimde yönteminin gövdesi olarak sahip yöntemi tanımı yaygındır.  Bu tür yöntemlerini kullanarak tanımlamak için bir söz dizimi kısayol yoktur `=>`:  
  
```csharp  
public Point Move(int dx, int dy) => new Point(x + dx, y + dy);   
public void Print() => Console.WriteLine(First + " " + Last);  
// Works with operators, properties, and indexers too.  
public static Complex operator +(Complex a, Complex b) => a.Add(b);  
public string Name => First + " " + Last;   
public Customer this[long id] => store.LookupCustomer(id);  
```  
  
 Yöntem döndürüyorsa `void` veya yönteminin gövdesi bir deyim ifadesi (aynı Lambda'lar gibi) olması gerekir async yöntemi.  Özellikler ve dizin oluşturucular için bunlar salt okunur olmalıdır ve kullanmadığınız `get` erişimci anahtar sözcüğü.  
  
## <a name="iterators"></a>Yineleyiciler  
 Yineleyici özel bir yineleme listesini veya bir dizi gibi bir koleksiyon üzerinden gerçekleştirir. Yineleyici kullanan [verim return](../../../csharp/language-reference/keywords/yield.md) her öğeye aynı anda geri dönmek için deyimi. Zaman bir [verim return](../../../csharp/language-reference/keywords/yield.md) deyimi ulaşıldığında geçerli kod konumda anımsanacak. Yineleyici sonraki çağrıldığında yürütme o konumdan yeniden başlatılır.  
  
 Yineleyici kullanarak istemci kodundan çağıran bir [foreach](../../../csharp/language-reference/keywords/foreach-in.md) deyimi.  
  
 Yineleyici dönüş türü olabilir <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, veya <xref:System.Collections.Generic.IEnumerator%601>.  
  
 Daha fazla bilgi için bkz: [yineleyiciler](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Sınıflar ve Yapılar](index.md)  
 [Erişim Değiştiricileri](access-modifiers.md)  
 [Statik Sınıflar ve Statik Sınıf Üyeleri](static-classes-and-static-class-members.md)  
 [Devralma](inheritance.md)  
 [Soyut ve Korumalı Sınıflar ve Sınıf Üyeleri](abstract-and-sealed-classes-and-class-members.md)  
 [params](../../../csharp/language-reference/keywords/params.md)  
 [return](../../../csharp/language-reference/keywords/return.md)  
 [out](../../../csharp/language-reference/keywords/out.md)  
 [ref](../../../csharp/language-reference/keywords/ref.md)  
 [Parametreleri Geçirme](passing-parameters.md)
