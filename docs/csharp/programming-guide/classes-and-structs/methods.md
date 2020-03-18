---
title: Yöntemler - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#]
- C# language, methods
ms.assetid: cc738f07-e8cd-4683-9585-9f40c0667c37
ms.openlocfilehash: 114fa2973c50be9a4199db9729e3cd9ea6122866
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77626535"
---
# <a name="methods-c-programming-guide"></a>Yöntemler (C# Programlama Kılavuzu)

Yöntem, bir dizi deyim içeren bir kod bloğudur. Program, yöntem çağırArak ve gerekli yöntem bağımsız değişkenlerini belirterek deyimlerin yürütülmesine neden olur. C#'da, çalıştırılan her yönerge bir yöntem bağlamında gerçekleştirilir. Yöntem, `Main` her C# uygulamasının giriş noktasıdır ve program başlatıldığında ortak dil çalışma süresi (CLR) olarak adlandırılır.

> [!NOTE]
> Bu makalede, adlandırılmış yöntemler anlatılmaktadır. Anonim işlevler hakkında bilgi için [Bkz. Anonim Fonksiyonlar.](../statements-expressions-operators/anonymous-functions.md)

## <a name="method-signatures"></a>Yöntem imzaları

Yöntemler, bir [sınıf,](../../language-reference/keywords/class.md) [yapı](../../language-reference/builtin-types/struct.md)veya [arabirim](../interfaces/index.md) gibi erişim düzeyi `public` veya `private`, iade değeri, `abstract` `sealed`yöntemin adı ve herhangi bir yöntem parametreleri gibi isteğe bağlı değiştiriciler belirterek bildirilir. Bu parçalar birlikte yöntemin imzasıdır.

> [!NOTE]
> Yöntemin dönüş türü, yöntem aşırı yükleme amacıyla yöntemin imzasının bir parçası değildir. Ancak, bir temsilci ve işaret ettiği yöntem arasındaki uyumluluğu belirlerken yöntemin imzasının bir parçasıdır.

Yöntem parametreleri parantez içinde eklenir ve virgülle ayrılır. Boş parantezler yöntemin parametre gerektirmediğini gösterir. Bu sınıf dört yöntem içerir:

[!code-csharp[csProgGuideObjects#40](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#40)]

## <a name="method-access"></a>Yöntem erişimi

Bir nesne üzerinde yöntem çağırmak, bir alana erişmek gibidir. Nesne adından sonra, bir nokta, yöntemin adını ekleyin ve parantez. Bağımsız değişkenler parantez içinde listelenir ve virgülle ayrılır. Bu nedenle `Motorcycle` sınıfın yöntemleri aşağıdaki örnekte olduğu gibi çağrılabilir:

[!code-csharp[csProgGuideObjects#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#41)]

## <a name="method-parameters-vs-arguments"></a>Yöntem parametreleri ve bağımsız değişkenler

Yöntem tanımı, gerekli parametrelerin adlarını ve türlerini belirtir. Kod çağırıldığında yöntem çağırır, her parametre için bağımsız değişken adı verilen somut değerler sağlar. Bağımsız değişkenler parametre türüyle uyumlu olmalıdır, ancak çağrı kodunda kullanılan bağımsız değişken adı (varsa) yöntemde tanımlanan parametreyle aynı olmak zorunda değildir. Örnek:

[!code-csharp[csProgGuideObjects#74](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#74)]

## <a name="passing-by-reference-vs-passing-by-value"></a>Referansa göre geçiş ve değere göre geçme

Varsayılan olarak, bir [değer türü](../../language-reference/builtin-types/value-types.md) örneği bir yönteme geçirildiğinde, kopya örneği kendisi yerine geçirilir. Bu nedenle, bağımsız değişkendeğişiklikleri arama yönteminde özgün örnek üzerinde hiçbir etkisi yoktur. Başvuru yla değer türü örneği geçmek `ref` için anahtar sözcüğü kullanın. Daha fazla bilgi için [Bkz. Değer Türü Parametreleri Geçme.](./passing-value-type-parameters.md)

Başvuru türünden bir nesne bir yönteme geçirildiğinde, nesneye bir başvuru geçirilir. Diğer bir zamanda, yöntem nesnenin kendisini değil, nesnenin konumunu gösteren bir bağımsız değişkeni alır. Bu başvuruyu kullanarak nesnenin bir üyesini değiştirirseniz, nesneyi değere göre geçirseniz bile değişiklik arama yöntemindeki bağımsız değişkene yansıtılır.

Aşağıdaki örnekte görüldüğü `class` gibi, anahtar kelimeyi kullanarak bir başvuru türü oluşturursunuz:

[!code-csharp[csProgGuideObjects#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#42)]

Şimdi, bu türe dayalı bir nesneyi bir yönteme geçirirseniz, nesneye bir başvuru geçirilir. Aşağıdaki örnek, yönteme `SampleRefType` `ModifyObject`bir tür nesnesi geçer:

[!code-csharp[csProgGuideObjects#75](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#75)]

Örnek, bir bağımsız değişkeni bir yönteme değer olarak geçirmesinde önceki örnekle temelde aynı şeyi yapar. Ancak, bir başvuru türü kullanıldığından, sonuç farklıdır. Parametre `ModifyObject` `value` alanında yapılan değişiklik, `obj`aynı zamanda yöntemde `value` `rt` `TestRefType` bağımsız değişkenalanını değiştirir. Yöntem `TestRefType` çıktı olarak 33 görüntüler.

Referans türlerinin başvuru ve değere göre nasıl geçirilen hakkında [Reference Types](../../language-reference/keywords/reference-types.md)daha fazla bilgi için [bkz.](./passing-reference-type-parameters.md)

## <a name="return-values"></a>Döndürülen değerler

Yöntemler arayana bir değer döndürebilir. İade türü, yöntem adından önce listelenen tür, değilse, `void`yöntem `return` anahtar sözcüğü kullanarak değeri döndürebilir. Anahtar kelimenin `return` ardından gelen bir değerin ardından gelen bir ifade, bu değeri yöntem arayana döndürecektir.

Değer, arayana değer veya C# 7.0 ile başlayarak [referans olarak](ref-returns.md)döndürülebilir. `ref` Anahtar kelime yöntem imzasında kullanılıyorsa ve her `return` anahtar kelimeyi izliyorsa, değerler başvuru tarafından arayanın döndürülür. Örneğin, aşağıdaki yöntem imza ve return deyimi, yöntemin `estDistance` arayana atıfta bulunarak bir değişken adlarını döndürür olduğunu gösterir.

```csharp
public ref double GetEstimatedDistance()
{
    return ref estDistance;
}
```

Anahtar `return` kelime de yöntemin yürütülmesini durdurur. İade türü ise, `void` `return` değeri olmayan bir deyim, yöntemin yürütülmesini durdurmak için yine de yararlıdır. `return` Anahtar kelime olmadan, yöntem kod bloğunun sonuna ulaştığında yürütmeyi durdurur. Geçersiz olmayan bir iade türüne sahip `return` yöntemlerin, bir değeri döndürmek için anahtar sözcüğü kullanması gerekir. Örneğin, bu iki yöntem, sonlu ları döndürmek için `return` anahtar sözcüğü kullanır:

[!code-csharp[csProgGuideObjects#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#44)]

Bir yöntemden döndürülen bir değeri kullanmak için, arama yöntemi nin kendisini her yerde aynı türde bir değerin yeterli olduğu her yerde çağırın yöntemini kullanabilir. İade değerini bir değişkene de atayabilirsiniz. Örneğin, aşağıdaki iki kod örneği aynı amacı gerçekleştirir:

[!code-csharp[csProgGuideObjects#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#45)]

[!code-csharp[csProgGuideObjects#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#46)]

Yerel bir değişkenkullanarak, bu `result`durumda, bir değeri depolamak için isteğe bağlıdır. Kodun okunabilirliğine yardımcı olabilir veya yöntemin tüm kapsamı için bağımsız değişkenin özgün değerini depolamanız gerekiyorsa gerekli olabilir.

Bir yöntemden referans la döndürülen bir değeri kullanmak için, değerini değiştirmek istiyorsanız [bir ref yerel](ref-returns.md#ref-locals) değişkeni bildirmeniz gerekir. Örneğin, `Planet.GetEstimatedDistance` yöntem başvuru yla <xref:System.Double> bir değer döndürürse, onu aşağıdaki gibi kodlu bir ref yerel değişkenolarak tanımlayabilirsiniz:

```csharp
ref int distance = plant
```

Bir yöntemden çok boyutlu bir `M`dizi döndürme, arama işlevi dizi geçti `M`eğer dizinin içeriğini değiştiren gerekli değildir.  İyi stil veya işlevsel `M` değerler akışı için elde edilen diziyi döndürebilirsiniz, ancak C# tüm başvuru türlerini değere göre geçtiği ve dizi referansının değeri diziişaretçisi olduğundan bu gerekli değildir. Yöntemde, `M`dizinin içeriğindeki herhangi bir değişiklik, aşağıdaki örnekte gösterildiği gibi, diziye başvuru olan herhangi bir kod tarafından gözlemlenebilir:

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

Daha fazla bilgi için [return'e](../../language-reference/keywords/return.md)bakın.

## <a name="async-methods"></a>Async yöntemleri

Async özelliğini kullanarak, açık geri aramalar kullanmadan veya kodunuzu birden çok yöntem veya lambda ifadeleri arasında el ile bölmeden eşzamanlı yöntemler çağırabilirsiniz.

Bir yöntemi [async](../../language-reference/keywords/async.md) değiştirici ile işaretlerseniz, yöntemde [bekleme](../../language-reference/operators/await.md) işlecini kullanabilirsiniz. Denetim async yönteminde bir bekleme ifadesine ulaştığında, denetim arayana döndürür ve beklenen görev tamamlanana kadar yöntemdeki ilerleme askıya alınır. Görev tamamlandığında, yürütme yöntemde devam edebilir.

> [!NOTE]
> Async yöntemi, henüz tamamlanmamış ilk beklenen nesneyle karşılaştığında veya önce hangisi gerçekleşirse async yönteminin sonuna geldiğinde arayanın karşısına geçer.

Bir async yöntemi <xref:System.Threading.Tasks.Task%601>, , <xref:System.Threading.Tasks.Task>veya geçersiz bir dönüş türü olabilir. Geçersiz dönüş türü öncelikle geçersiz dönüş türünün gerekli olduğu olay işleyicilerini tanımlamak için kullanılır. Geçersiz liği döndüren bir async yöntemi beklenebilir ve boşluk döndüren bir yöntemin arayan ı, yöntemin attığı özel durumları yakalayamaz.

Aşağıdaki örnekte, `DelayAsync` bir dönüş türü olan bir <xref:System.Threading.Tasks.Task%601>async yöntemidir. `DelayAsync`bir `return` tamsayı döndüren bir ifadesi vardır. Bu nedenle yöntem `DelayAsync` bildirimibir `Task<int>`dönüş türü olmalıdır . İade türü `Task<int>`olduğundan, aşağıdaki ifadenin gösterdiği gibi bir insalı `await` `DoSomethingAsync` üretir `int result = await delayTask`ifadenin değerlendirilmesi: .

Yöntem, `startButton_Click` bir boşluk dönüş türü olan bir async yönteminin bir örneğidir. Async yöntemi `DoSomethingAsync` olduğundan, aşağıdaki ifadede `DoSomethingAsync` görüldüğü gibi, çağrı için görev `await DoSomethingAsync();`in beklenmesi gerekir: . `startButton_Click` Yöntem bir `await` ifade olduğundan yöntem `async` değiştirici ile tanımlanmalıdır.

[!code-csharp[csAsyncMethod#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csasyncmethod/cs/mainwindow.xaml.cs#2)]

Bir async yöntemi herhangi bir [ref](../../language-reference/keywords/ref.md) veya [çıkış](../../language-reference/keywords/out-parameter-modifier.md) parametreleri bildiremez, ancak bu tür parametrelere sahip yöntemleri çağırabilir.

Async yöntemleri hakkında daha fazla bilgi için, [async ile Asynchronous Programlama](../concepts/async/index.md)bakın ve bekliyor , [Async Programları Kontrol Akışı](../concepts/async/control-flow-in-async-programs.md), ve [Async İade Türleri](../concepts/async/async-return-types.md).

## <a name="expression-body-definitions"></a>İfade gövdesi tanımları

Yalnızca bir ifadenin sonucuyla hemen dönen veya yöntemin gövdesi olarak tek bir ifadeye sahip yöntem tanımlarına sahip olması yaygındır. Bu tür yöntemleri tanımlamak için bir sözdizimi kısayolu vardır: `=>`

```csharp
public Point Move(int dx, int dy) => new Point(x + dx, y + dy);
public void Print() => Console.WriteLine(First + " " + Last);
// Works with operators, properties, and indexers too.
public static Complex operator +(Complex a, Complex b) => a.Add(b);
public string Name => First + " " + Last;
public Customer this[long id] => store.LookupCustomer(id);
```

Yöntem döndürür `void` veya bir async yöntemi ise, o zaman yöntemin gövdesi bir deyim ifadesi olmalıdır (lambdas ile aynı). Özellikler ve dizin leyiciler için yalnızca okunması gerekir ve `get` erişimci anahtar sözcüğü kullanmazsınız.

## <a name="iterators"></a>Yineleyiciler

Yineleyici, liste veya dizi gibi bir koleksiyon üzerinde özel bir yineleme gerçekleştirir. Bir yineleyici, her öğeyi birer birer döndürmek için [verim iade](../../language-reference/keywords/yield.md) deyimini kullanır. Bir [verim iade](../../language-reference/keywords/yield.md) deyimine ulaşıldığında, koddaki geçerli konum hatırlanır. Yineleyici bir sonraki seferde çağrıldığında yürütme bu konumdan yeniden başlatılır.

[Her](../../language-reference/keywords/foreach-in.md) bir deyim kullanarak istemci kodundan bir yineleyici çağırırsınız.

Bir yineleyicinin dönüş türü <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, <xref:System.Collections.Generic.IEnumerator%601>veya .

Daha fazla bilgi için [bkz.](../concepts/iterators.md)

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve Structs](index.md)
- [Erişim Değiştiricileri](access-modifiers.md)
- [Statik Sınıflar ve Statik Sınıf Üyeleri](static-classes-and-static-class-members.md)
- [Devralma](inheritance.md)
- [Soyut ve Korumalı Sınıflar ve Sınıf Üyeleri](abstract-and-sealed-classes-and-class-members.md)
- [params](../../language-reference/keywords/params.md)
- [return](../../language-reference/keywords/return.md)
- [çıkış](../../language-reference/keywords/out.md)
- [Referans](../../language-reference/keywords/ref.md)
- [Parametreleri Geçirme](passing-parameters.md)
