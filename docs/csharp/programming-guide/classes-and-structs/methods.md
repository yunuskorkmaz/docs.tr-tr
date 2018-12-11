---
title: Yöntemleri - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#]
- C# language, methods
ms.assetid: cc738f07-e8cd-4683-9585-9f40c0667c37
ms.openlocfilehash: df2d7837217f4267f95ed73948a4eb479cc035c1
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53244420"
---
# <a name="methods-c-programming-guide"></a>Yöntemler (C# Programlama Kılavuzu)
Bir dizi deyim içeren kod bloğu bir yöntemdir. Bir program yöntemini çağırarak ve tüm gerekli metot bağımsız değişkenleri belirtme yürütülecek deyimler neden olur. C# içinde yürütülen her yönerge bir yöntem bağlamında gerçekleştirilir. Main yöntemi her C# uygulaması için giriş noktasıdır ve programı başlatıldığında ortak dil çalışma zamanı tarafından (CLR) çağrılır.  
  
> [!NOTE]
>  Bu konuda, adlandırılmış yöntemler anlatılmaktadır. Anonim işlevler hakkında daha fazla bilgi için bkz: [anonim işlevler](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).  
  
## <a name="method-signatures"></a>Yöntem imzaları  
 Yöntem içinde bildirilen bir [sınıfı](../../../csharp/language-reference/keywords/class.md) veya [yapı](../../../csharp/language-reference/keywords/struct.md) erişim düzeyi gibi belirterek `public` veya `private`, gibi isteğe bağlı değiştiricilere `abstract` veya `sealed`, dönüş değeri, yöntem ve herhangi bir yöntem parametre adı. Bu bölümleri metodun imzası birleştirilir.  
  
> [!NOTE]
>  Bir yöntemin dönüş türü yöntemi aşırı yükleme amaçları için yöntem imzasının bir parçası değil. Ancak, bir temsilci ve işaret yöntemi arasındaki uyumluluk belirlerken metodun imzası bir parçası olur.  
  
 Yöntem parametreleri ayraç içine alınır ve virgülle ayrılır. Boş ayraçlar yöntemi hiçbir parametre gerektirmiyor gösterir. Bu sınıf, dört yöntemler içerir:  
  
 [!code-csharp[csProgGuideObjects#40](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_1.cs)]  
  
## <a name="method-access"></a>Metot erişimini  
 Bir nesne üzerinde bir yöntemi çağırmak için bir alan erişme gibi olur. Nesne adından sonra bir nokta, adı yöntemi ve parantez ekleyin. Bağımsız değişkenler, parantez içinde listelenir ve virgülle ayrılır. Yöntemlerinin `Motorcycle` sınıfı bu nedenle aşağıdaki örnekte olduğu gibi çağrılabilir:  
  
 [!code-csharp[csProgGuideObjects#41](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_2.cs)]  
  
## <a name="method-parameters-vs-arguments"></a>Yöntem parametreleri vs. Arguments  
 Yöntem tanımını adlarını ve türlerini, gerekli olan herhangi bir parametre belirtir. Kod çağrıları metodu çağrılırken, her parametresi için bağımsız değişken olarak adlandırılan somut değerleri sağlar. Bağımsız değişken parametre türü ile uyumlu olması gerekir ancak çağıran kod içinde kullanılan bir bağımsız değişken adı (varsa) aynı adlı bir parametre olarak yönteminde tanımlanmış olması gerekmez. Örneğin:  
  
 [!code-csharp[csProgGuideObjects#74](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_3.cs)]  
  
## <a name="passing-by-reference-vs-passing-by-value"></a>Başvuru vs geçirerek. Değere göre geçirme  
 Varsayılan olarak, bir değer türü bir yönteme geçildiğinde bir kopyasını nesne yerine geçirilir. Bu nedenle, değişiklikleri bağımsız değişkene, çağırma yöntemi özgün kopyası üzerinde etkisi yoktur. Ref anahtar sözcüğü kullanılarak başvuruya göre bir değer türü geçirebilirsiniz. Daha fazla bilgi için [değer türü parametrelerini geçirme](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md). Yerleşik türlerin listesi için bkz. [değer türleri tablosu](../../../csharp/language-reference/keywords/value-types-table.md).  
  
 Nesnesine bir başvuru, başvuru türünde bir nesne bir yönteme geçildiğinde geçirilir. Diğer bir deyişle, yöntem, nesnenin kendisini değil, ancak nesnenin konumu gösteren bir bağımsız değişken alır. Bu başvuruyu kullanarak bir nesnenin üyesi değiştirirseniz, nesne değişkeni değer olarak bile değişiklik çağırma yöntemi bağımsız değişken yansıtılır.  
  
 Bir başvuru türü kullanarak oluşturduğunuz `class` anahtar sözcüğü, aşağıdaki örnekte gösterildiği gibi.  
  
 [!code-csharp[csProgGuideObjects#42](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_4.cs)]  
  
 Şimdi, bu tür bir yönteme temel alan bir nesne geçirirseniz, nesnesine bir başvuru geçirilir. Aşağıdaki örnek, türü bir nesne geçirir `SampleRefType` yöntemine `ModifyObject`.  
  
 [!code-csharp[csProgGuideObjects#75](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_5.cs)]  
  
 Bu bağımsız değişken değerine göre bir yönteme geçirir, örnek önceki örnekteki gibi temelde aynı şeyi yapar. Ancak, bir başvuru türü kullanıldığından sonucu farklıdır. İçinde yapılan değişikliği `ModifyObject` için `value` parametre alanını `obj`, ayrıca değiştirir `value` bağımsız değişken alan `rt`, `TestRefType` yöntemi. `TestRefType` Yöntemi 33 çıkış olarak görüntüler.  
  
 Başvuru türleri başvuruya göre ve değere göre geçirilecek hakkında daha fazla bilgi için bkz. [başvuru türü parametreleri geçirme](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md) ve [başvuru türleri](../../../csharp/language-reference/keywords/reference-types.md).  
  
## <a name="return-values"></a>Dönüş Değerleri  
Yöntemler, çağırana bir değer döndürebilir. Dönüş türü, yöntem adından önce listelenen bir tür değil `void`, yöntem kullanarak değer döndürebilir `return` anahtar sözcüğü. With deyimi `return` dönüş türüyle eşleşen bir değere göre anahtar sözcüğünü yöntemi çağırana değeri döndürür. 

Değeri, çağırana değeri veya C# 7.0 ile başlayan tarafından döndürülebilir [başvuruya göre](ref-returns.md). Değerleri çağırana döndürülen başvuruya göre `ref` anahtar sözcüğü Yöntem imzasında kullanılan ve her takip eden `return` anahtar sözcüğü. Örneğin, aşağıdaki yöntemi imza ve dönüş deyimi belirtmek yöntem bir değişken adları döndürür `estDistance` çağırana başvuruya göre.

```csharp
public ref double GetEstimatedDistance()
{
   return ref estDistance;
}
```

`return` Anahtar sözcüğü de yöntemin yürütülmesini durdurur. Dönüş türü ise `void`, `return` deyimi bir değer olmadan, yöntemin yürütülmesini durdurmak yine de kullanışlıdır. Olmadan `return` anahtar sözcüğü, yöntem durdurur kod bloğunun sonuna ulaştığında yürütülüyor. Yöntemleriyle void olmayan dönüş türü kullanmak için gerekli `return` bir değer döndürmek için anahtar sözcüğü. Örneğin, bu iki yöntem kullanmak `return` anahtar sözcüğü, tamsayı döndüren için:  
  
 [!code-csharp[csProgGuideObjects#44](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_6.cs)]  
  
 Yöntemi tarafından döndürülen bir değer kullanmak için yöntemi çağrılırken, aynı türde bir değer yeterli yöntemi çağrının kendisini her yerde kullanabilirsiniz. Ayrıca, dönüş değeri bir değişkene atayabilirsiniz. Örneğin, aşağıdaki iki kod örnekleri ve aynı hedefe ulaşmak:  
  
 [!code-csharp[csProgGuideObjects#45](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_7.cs)]  
  
 [!code-csharp[csProgGuideObjects#46](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_8.cs)]  
  
 Yerel değişken, bu durumda, kullanarak `result`depolamak için bir değer isteğe bağlıdır. Yöntemin tüm kapsam için bağımsız değişkenin özgün değeri depolamak gerekiyorsa gerekli olabilir veya kodun okunabilirliğini yardımcı olabilir.  

Bir yönteme başvuru tarafından döndürülen bir değer kullanmak için size bildirmelidir bir [ref yerel](ref-returns.md#ref-locals) değeri değiştirmek istiyorsanız, değişken. Örneğin, varsa `Planet.GetEstimatedDistance` yöntemi döndürür bir <xref:System.Double> değere Başvuruya göre bunu aşağıdaki gibi kod ile bir ref yerel değişken tanımlayabilirsiniz:

```csharp
ref int distance = plant 
```

Çok boyutlu bir dizi döndüren bir yöntemi, `M`, dizinin değiştiren içeriği çağıran işlevin diziye aktarılırsa gerekli olmadığı `M`.  Sonuçta elde edilen diziden döndürebilir `M` iyi stil veya değerler, ancak işlev akışını C# değere göre tüm başvuru türleri geçirir ve bir dizi başvuru değeri dizi işaretçisi olduğundan gerekli değildir. Yönteminde `M`, aşağıdaki örnekte gösterildiği gibi dizi için bir başvuruya sahip herhangi bir kod tarafından takip edilebilir olmasını dizinin içeriğini herhangi bir değişiklik olan.  
  
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
  
 Daha fazla bilgi için [dönüş](../../../csharp/language-reference/keywords/return.md).  
  
## <a name="async-methods"></a>Zaman uyumsuz yöntemler  
 Zaman uyumsuz özelliğini kullanarak, açık geri çağırmaları kullanarak veya kodunuzun birden çok yöntemlerde veya lambda ifadelerinde el ile bölme olmadan zaman uyumsuz yöntemler çağırabilirsiniz. 
  
 Bir yöntem ile işaretlerseniz [zaman uyumsuz](../../../csharp/language-reference/keywords/async.md) kullanabileceğiniz değiştiricisi [await](../../../csharp/language-reference/keywords/await.md) yönteminde işleci. Denetim, zaman uyumsuz yöntemdeki bir await ifadesine ulaştığında, Denetim çağırana döner ve awaited görevi tamamlanıncaya kadar yöntemin ediyor askıya alındı. Görev tamamlandığında, yürütme yönteminde devam edebilir.  
  
> [!NOTE]
>  Henüz tamamlanmadı ilk beklenen nesne karşılaşır veya zaman uyumsuz yöntemin sonuna alır, zaman uyumsuz yöntemini çağırana döner hangisi önce gerçekleşirse.  
  
 Bir zaman uyumsuz yöntem dönüş türüne sahip olabilir <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>, veya void. Dönüş türü void dönüş türü void gerekli olduğu olay işleyicilerini tanımlamak için öncelikle kullanılır. Void döndüren bir zaman uyumsuz yöntem beklenemez ve void döndüren bir yöntemi çağıran kişi, yöntemin oluşturduğu özel durumları yakalayamaz.  
  
 Aşağıdaki örnekte, `DelayAsync` dönüş türüne sahip bir zaman uyumsuz yöntem <xref:System.Threading.Tasks.Task%601>. `DelayAsync` sahip bir `return` deyimi bir tamsayı döndürür. Bu nedenle yöntemi bildirimini `DelayAsync` dönüş türüne sahip olmalıdır `Task<int>`. Dönüş türü olduğundan `Task<int>`, değerlendirmesi `await` ifadesinde `DoSomethingAsync` aşağıdaki deyimi gösterildiği gibi bir tamsayı üretir: `int result = await delayTask`.  
  
 `startButton_Click` Yöntemi, bir zaman uyumsuz yöntemin dönüş türü void olan bir örnek verilmiştir. Çünkü `DoSomethingAsync` bir zaman uyumsuz yöntem çağrısı için görev `DoSomethingAsync` , aşağıdaki deyimi gösterildiği gibi beklenmesini gerekir: `await DoSomethingAsync();`. `startButton_Click` Yöntemi ile tanımlanmalıdır `async` değiştirici yöntemi sahip olduğu bir `await` ifade.  
  
 [!code-csharp[csAsyncMethod#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_9.cs)]  
  
 Herhangi bir zaman uyumsuz yöntem bildiremezsiniz [ref](../../../csharp/language-reference/keywords/ref.md) veya [kullanıma](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametreleri, ancak bu tür parametreleri olan yöntemleri çağırabilir.  
  
 Zaman uyumsuz yöntemler hakkında daha fazla bilgi için bkz. [Asynchronous Programming with async ve await](../../../csharp/programming-guide/concepts/async/index.md), [zaman uyumsuz programlarda akış kontrolü](../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md), ve [Async Return Types](../../../csharp/programming-guide/concepts/async/async-return-types.md).  
  
## <a name="expression-body-definitions"></a>İfade gövdesi tanımları  
 Yalnızca hemen bir ifade sonucunu döndürür veya Yöntemin gövdesi tek bir deyimde olan yöntem tanımlarını yaygındır.  Kullanarak bu yöntemleri tanımlamak için bir söz dizimi kısayolu yok `=>`:  
  
```csharp  
public Point Move(int dx, int dy) => new Point(x + dx, y + dy);   
public void Print() => Console.WriteLine(First + " " + Last);  
// Works with operators, properties, and indexers too.  
public static Complex operator +(Complex a, Complex b) => a.Add(b);  
public string Name => First + " " + Last;   
public Customer this[long id] => store.LookupCustomer(id);  
```  
  
 Yöntem döndürüyorsa `void` veya Yöntemin gövdesi bir deyim ifadesi (aynı lambdalar gibi) olmalıdır. bir zaman uyumsuz yöntem.  Özellikler ve dizin oluşturucular için bunlar salt okunur olmalıdır ve kullanmadığınız `get` erişimci anahtar sözcüğü.  
  
## <a name="iterators"></a>Yineleyiciler  
 Bir yineleyici listesini veya bir dizi gibi bir koleksiyon üzerinde özel yineleme gerçekleştirir. Yineleyici [yield return](../../../csharp/language-reference/keywords/yield.md) her öğeyi bir defada döndürmek için deyimi. Olduğunda bir [yield return](../../../csharp/language-reference/keywords/yield.md) deyimine ulaşıldığında, kodun geçerli konumu anımsanacak. Yürütme, yineleyici sonraki sefer çağrıldığında bu konumdan yeniden başlatılır.  
  
 Bir yineleyici kullanarak istemci koddan çağırmak bir [foreach](../../../csharp/language-reference/keywords/foreach-in.md) deyimi.  
  
 Dönüş türü bir yineleyicinin olabilir <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, veya <xref:System.Collections.Generic.IEnumerator%601>.  
  
 Daha fazla bilgi için [yineleyiciler](../../../csharp/programming-guide/concepts/iterators.md).  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [Sınıflar ve Yapılar](index.md)  
- [Erişim Değiştiricileri](access-modifiers.md)  
- [Statik Sınıflar ve Statik Sınıf Üyeleri](static-classes-and-static-class-members.md)  
- [Devralma](inheritance.md)  
- [Soyut ve Korumalı Sınıflar ve Sınıf Üyeleri](abstract-and-sealed-classes-and-class-members.md)  
- [params](../../../csharp/language-reference/keywords/params.md)  
- [return](../../../csharp/language-reference/keywords/return.md)  
- [out](../../../csharp/language-reference/keywords/out.md)  
- [ref](../../../csharp/language-reference/keywords/ref.md)  
- [Parametreleri Geçirme](passing-parameters.md)
