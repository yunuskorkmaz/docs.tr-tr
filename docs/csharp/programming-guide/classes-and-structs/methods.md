---
title: Yöntemler- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#]
- C# language, methods
ms.assetid: cc738f07-e8cd-4683-9585-9f40c0667c37
ms.openlocfilehash: 7255d4a2c57ea9e0469174cfe139a4ab54d62372
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596401"
---
# <a name="methods-c-programming-guide"></a>Yöntemler (C# Programlama Kılavuzu)
Yöntemi, bir dizi deyim içeren bir kod bloğudur. Program, metodu çağırarak ve gerekli Yöntem bağımsız değişkenlerini belirterek deyimlerin yürütülmesine neden olur. ' C#De, her yürütülen yönerge bir yöntem bağlamında gerçekleştirilir. Main yöntemi her C# uygulamanın giriş noktasıdır ve program başlatıldığında ortak dil çalışma zamanı (CLR) tarafından çağrılır.  
  
> [!NOTE]
>  Bu konuda adlandırılmış yöntemler ele alınmaktadır. Anonim işlevler hakkında daha fazla bilgi için bkz. [Anonim işlevler](../statements-expressions-operators/anonymous-functions.md).  
  
## <a name="method-signatures"></a>Yöntem Imzaları  
 Yöntemler veya, dönüş değeri, yöntemin [](../../language-reference/keywords/struct.md) adı ve herhangi bir yöntem parametresi gibi erişim `public` düzeyi `private`belirtilerek, `abstract` veya gibi isteğe bağlı `sealed`değiştiriciler belirtilerek bir [sınıf](../../language-reference/keywords/class.md) veya yapı içinde bildirilmiştir. . Bu parçalar, yönteminin imzasıdır.  
  
> [!NOTE]
>  Bir yöntemin dönüş türü, yöntem aşırı yüklemesi amaçları için yöntemin imzasının bir parçası değildir. Ancak, bir temsilci ve işaret ettiği yöntem arasındaki uyumluluğun belirlenmesi sırasında yönteminin imzasının bir parçasıdır.  
  
 Yöntem parametreleri parantez içine alınır ve virgülle ayrılır. Boş parantezler, yöntemin hiçbir parametre gerektirmediğini belirtir. Bu sınıf dört yöntem içerir:  
  
 [!code-csharp[csProgGuideObjects#40](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#40)]  
  
## <a name="method-access"></a>Yöntem erişimi  
 Bir nesne üzerinde bir yöntemi çağırmak, bir alana erişme gibidir. Nesne adından sonra bir nokta, yöntemin adı ve parantez ekleyin. Bağımsız değişkenler parantez içinde listelenir ve virgülle ayrılır. Bu nedenle, `Motorcycle` sınıfının yöntemleri aşağıdaki örnekte olduğu gibi çağrılabilir:  
  
 [!code-csharp[csProgGuideObjects#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#41)]  
  
## <a name="method-parameters-vs-arguments"></a>Yöntem parametreleri ile Arguments  
 Yöntem tanımı, gerekli parametrelerin adlarını ve türlerini belirtir. Kodu çağırırken yöntemi çağırdığında, her parametre için bağımsız değişkenler olarak adlandırılan somut değerler sağlar. Bağımsız değişkenlerin parametre türüyle uyumlu olması gerekir, ancak çağıran kodda kullanılan bağımsız değişken adı (varsa) yöntemde tanımlanan parametre ile aynı olmak zorunda değildir. Örneğin:  
  
 [!code-csharp[csProgGuideObjects#74](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#74)]  
  
## <a name="passing-by-reference-vs-passing-by-value"></a>Başvuruya göre geçirme ile Değere göre geçirme  
 Varsayılan olarak, bir değer türü bir yönteme geçirildiğinde nesnenin kendisi yerine bir kopya geçirilir. Bu nedenle, bağımsız değişkende yapılan değişikliklerin, çağırma yönteminde orijinal kopya üzerinde hiçbir etkisi yoktur. Ref anahtar sözcüğünü kullanarak bir değer türü başvuruya göre geçirebilirsiniz. Daha fazla bilgi için bkz. [değer türü parametrelerini geçirme](./passing-value-type-parameters.md). Yerleşik değer türlerinin bir listesi için bkz. [değer türleri tablosu](../../language-reference/keywords/value-types-table.md).  
  
 Başvuru türündeki bir nesne yöntemine geçirildiğinde, nesnesine bir başvuru geçirilir. Diğer bir deyişle, yöntem nesnenin kendisini değil, nesnenin konumunu gösteren bir bağımsız değişken alır. Bu başvuruyu kullanarak nesnesinin bir üyesini değiştirirseniz, nesneyi değere göre iletseniz bile, değişiklik çağırma yöntemindeki bağımsız değişkende yansıtılır.  
  
 Aşağıdaki örnekte gösterildiği gibi `class` anahtar sözcüğünü kullanarak bir başvuru türü oluşturursunuz.  
  
 [!code-csharp[csProgGuideObjects#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#42)]  
  
 Artık, bu türü temel alan bir nesneyi bir yönteme geçirirseniz, nesnesine bir başvuru geçirilir. Aşağıdaki örnek, türünde `SampleRefType` bir nesnesini yöntemine `ModifyObject`geçirir.  
  
 [!code-csharp[csProgGuideObjects#75](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#75)]  
  
 Örnek temelde bir yönteme değere göre bir bağımsız değişken geçirdiğinden önceki örnekle aynı şeyi yapar. Ancak, bir başvuru türü kullanıldığından, sonuç farklıdır. Parametresinin `ModifyObject` `value` alanıüzerindeyapılan`value` değişiklik `rt`, yöntemi`TestRefType` içindeki bağımsız değişkenin alanını da değiştirir. `obj` `TestRefType` Yöntemi çıkış olarak 33 görüntüler.  
  
 Başvuru türlerini başvuruya ve değere göre geçirme hakkında daha fazla bilgi için bkz. [başvuru türü parametrelerini](./passing-reference-type-parameters.md) ve [başvuru türlerini](../../language-reference/keywords/reference-types.md)geçirme.  
  
## <a name="return-values"></a>Dönüş Değerleri  
Yöntemler çağırana bir değer döndürebilir. Dönüş türü, yöntem adından önce listelenen tür değilse `void`, yöntemi `return` anahtar sözcüğünü kullanarak değeri döndürebilir. Dönüş türüyle eşleşen bir `return` değer gelen anahtar sözcüğünü içeren bir ifade, bu değeri çağıran metoda döndürür. 

Değer, çağırarak değere göre veya 7,0 ile C# başlayarak [başvuruya göre](ref-returns.md)döndürülebilir. `ref` Anahtar sözcüğü Yöntem imzasında kullanılıyorsa ve her `return` bir anahtar sözcüğü izliyorsa, değerler, çağıran başvuruya göre döndürülür. Örneğin, aşağıdaki yöntem imzası ve Return deyimleri, yöntemin çağırana başvuruya göre değişken adlarını `estDistance` döndürdüğünü gösterir.

```csharp
public ref double GetEstimatedDistance()
{
   return ref estDistance;
}
```

`return` Anahtar sözcüğü, yönteminin yürütülmesini de sonlandırır. Dönüş türü ise `void`, değeri olmayan bir `return` ifade, metodun yürütülmesini durdurmak için hala yararlıdır. `return` Anahtar sözcüğü olmadan Yöntem, kod bloğunun sonuna ulaştığında yürütmeyi durdurur. Bir değer döndürmek için `return` anahtar sözcüğünü kullanmak için void olmayan bir dönüş türüne sahip metotlar gereklidir. Örneğin, bu iki yöntem tamsayılar döndürmek için `return` anahtar sözcüğünü kullanır:  
  
 [!code-csharp[csProgGuideObjects#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#44)]  
  
 Bir yöntemden döndürülen bir değer kullanmak için, çağırma yöntemi yöntemi tek bir değer olan her yerde, aynı türde bir değer yeterli olacak şekilde kullanabilir. Dönüş değerini bir değişkene de atayabilirsiniz. Örneğin, aşağıdaki iki kod örneği aynı hedefi yerine getirmektedir:  
  
 [!code-csharp[csProgGuideObjects#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#45)]  
  
 [!code-csharp[csProgGuideObjects#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#46)]  
  
 Bu durumda `result`, bir değeri depolamak için yerel bir değişken kullanmak isteğe bağlıdır. Kodun okunabilirliğini yardımcı olabilir veya metodun tüm kapsamı için bağımsız değişkenin özgün değerini depolamanız gerekirse gerekli olabilir.  

Bir yöntemden başvuruya göre döndürülen bir değeri kullanmak için, değerini değiştirmek istiyorsanız bir [ref yerel](ref-returns.md#ref-locals) değişkeni bildirmeniz gerekir. Örneğin, `Planet.GetEstimatedDistance` yöntemi başvuruya göre bir <xref:System.Double> değer döndürürse, bunu aşağıdaki gibi kodla bir ref yerel değişkeni olarak tanımlayabilirsiniz:

```csharp
ref int distance = plant 
```

Arama işlevi diziyi içine `M` `M`geçirse, dizinin içeriğini değiştiren bir yöntemden çok boyutlu bir dizi döndürülüyor.  Elde edilen diziyi, iyi stil veya `M` işlevsel akış için ' den döndürebilirsiniz, ancak bu gerekli değildir çünkü C# tüm başvuru türlerini değere göre geçirir ve dizi başvurusunun değeri dizi işaretçisidir. Yönteminde `M`, dizideki içeriklerinde yapılan tüm değişiklikler, aşağıdaki örnekte gösterildiği gibi diziye başvuran herhangi bir kod tarafından Observable ' tır.  
  
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
  
 Daha fazla bilgi için bkz. [Return](../../language-reference/keywords/return.md).  
  
## <a name="async-methods"></a>Zaman uyumsuz yöntemler  
 Async özelliğini kullanarak, açık geri çağırmaları kullanmadan zaman uyumsuz yöntemleri çağırabilir veya kodunuzu birden çok yöntemde veya Lambda ifadelerinde el ile böedebilirsiniz. 
  
 [Zaman uyumsuz](../../language-reference/keywords/async.md) değiştiriciyle bir yöntemi işaretlerseniz, yönteminde [await](../../language-reference/keywords/await.md) işlecini kullanabilirsiniz. Denetim zaman uyumsuz yöntemde bir await ifadesine ulaştığında denetim çağırana döner ve beklenen görev tamamlanana kadar yöntemdeki ilerleme durumu askıya alınır. Görev tamamlandığında, yürütme yöntemi içinde çalışmaya çalışabilir.  
  
> [!NOTE]
>  Zaman uyumsuz bir yöntem, henüz tamamlanmamış olan ilk beklemiş nesneyle karşılaştığında çağırana döner veya zaman uyumsuz yöntemin sonuna kadar, hangisi önce gerçekleşiyorsa.  
  
 Zaman uyumsuz bir yöntem <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>, veya void dönüş türüne sahip olabilir. Void dönüş türü birincil olarak, bir void dönüş türünün gerekli olduğu olay işleyicilerini tanımlamak için kullanılır. Void döndüren zaman uyumsuz bir yöntem beklenemez ve void döndüren bir yöntemi çağıran yöntemin aldığı özel durumları yakalayamaz.  
  
 Aşağıdaki örnekte, `DelayAsync` dönüş <xref:System.Threading.Tasks.Task%601>türüne sahip bir zaman uyumsuz yöntem. `DelayAsync`, bir `return` tamsayı döndüren bir ifadeye sahiptir. Bu nedenle, öğesinin `DelayAsync` yöntem bildirimi bir dönüş `Task<int>`türüne sahip olmalıdır. Dönüş türü olduğu için, `Task<int>`içindeki `await` `DoSomethingAsync` ifadesinin değerlendirmesi aşağıdaki deyim tarafından gösterildiği gibi bir tamsayı oluşturur: `int result = await delayTask`.  
  
 `startButton_Click` Yöntemi, void dönüş türüne sahip bir zaman uyumsuz metoda bir örnektir. Zaman `DoSomethingAsync` uyumsuz bir yöntem olduğundan, `DoSomethingAsync` çağrının görevi beklenmelidir, çünkü aşağıdaki deyimde gösterildiği gibi: `await DoSomethingAsync();`. Metodun `startButton_Click` `async` bir ifadesi`await` olduğundan, metodun değiştirici ile tanımlanması gerekir.  
  
 [!code-csharp[csAsyncMethod#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csasyncmethod/cs/mainwindow.xaml.cs#2)]  
  
 Zaman uyumsuz bir yöntem herhangi bir [ref](../../language-reference/keywords/ref.md) veya [Out](../../language-reference/keywords/out-parameter-modifier.md) parametresi bildiremez, ancak bu parametrelere sahip yöntemleri çağırabilir.  
  
 Zaman uyumsuz yöntemler hakkında daha fazla bilgi için bkz. [Async ve await Ile zaman uyumsuz programlama](../concepts/async/index.md), [zaman uyumsuz programlarda denetim akışı](../concepts/async/control-flow-in-async-programs.md)ve [zaman uyumsuz dönüş türleri](../concepts/async/async-return-types.md).  
  
## <a name="expression-body-definitions"></a>İfade gövdesi tanımları  
 Yalnızca bir ifadenin sonucuyla hemen dönen veya yöntemin gövdesi olarak tek bir deyimi olan yöntem tanımlarının olması yaygındır.  Kullanarak `=>`bu tür yöntemleri tanımlamaya yönelik bir sözdizimi kısayolu vardır:  
  
```csharp  
public Point Move(int dx, int dy) => new Point(x + dx, y + dy);   
public void Print() => Console.WriteLine(First + " " + Last);  
// Works with operators, properties, and indexers too.  
public static Complex operator +(Complex a, Complex b) => a.Add(b);  
public string Name => First + " " + Last;   
public Customer this[long id] => store.LookupCustomer(id);  
```  
  
 Yöntemi bir zaman uyumsuz `void` yöntem döndürürse veya ise, yöntemin gövdesi bir deyim ifadesi olmalıdır (Lambdalar ile aynı).  Özellikler ve Dizin oluşturucular için, bunların salt okunmaları ve `get` erişimci anahtar sözcüğünü kullanmanız gerekir.  
  
## <a name="iterators"></a>Yineleyiciler  
 Yineleyici, bir koleksiyon üzerinde liste veya dizi gibi özel bir yineleme gerçekleştirir. Bir yineleyici, her öğeyi birer birer döndürmek için [yield return](../../language-reference/keywords/yield.md) ifadesini kullanır. Bir [yield return](../../language-reference/keywords/yield.md) ifadesine ulaşıldığında, koddaki geçerli konum hatırlanır. Yineleyici bir sonraki sefer çağrıldığında, yürütme o konumdan yeniden başlatılır.  
  
 Bir [foreach](../../language-reference/keywords/foreach-in.md) ifadesi kullanarak istemci kodundan bir yineleyici çağırın.  
  
 Yineleyicinin <xref:System.Collections.IEnumerable>dönüş türü <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.IEnumerator>,,, veya <xref:System.Collections.Generic.IEnumerator%601>olabilir.  
  
 Daha fazla bilgi için bkz. [yineleyiciler](../concepts/iterators.md).  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve Yapılar](index.md)
- [Erişim Değiştiricileri](access-modifiers.md)
- [Statik Sınıflar ve Statik Sınıf Üyeleri](static-classes-and-static-class-members.md)
- [Devralma](inheritance.md)
- [Soyut ve Korumalı Sınıflar ve Sınıf Üyeleri](abstract-and-sealed-classes-and-class-members.md)
- [params](../../language-reference/keywords/params.md)
- [return](../../language-reference/keywords/return.md)
- [out](../../language-reference/keywords/out.md)
- [ref](../../language-reference/keywords/ref.md)
- [Parametreleri Geçirme](passing-parameters.md)
