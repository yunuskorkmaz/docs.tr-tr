---
title: using deyimleri-C# başvurusu
ms.date: 04/07/2020
helpviewer_keywords:
- using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
ms.openlocfilehash: 3c479faeeb66865b8c368edba881429a7cb956ec
ms.sourcegitcommit: 5988e9a29cedb8757320817deda3c08c6f44a6aa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2020
ms.locfileid: "82199683"
---
# <a name="using-statement-c-reference"></a>using deyimleri (C# Başvurusu)

<xref:System.IDisposable> Nesnelerin doğru kullanımını sağlayan uygun bir sözdizimi sağlar. C# 8,0 ' `using` den başlayarak, ifade <xref:System.IAsyncDisposable> nesnelerin doğru kullanımını sağlar.

## <a name="example"></a>Örnek

Aşağıdaki örnek, `using` ifadesinin nasıl kullanılacağını göstermektedir.

:::code language="csharp" source="snippets/usings.cs" id="SnippetFirstExample":::

C# 8,0 ' den başlayarak, küme ayraçları gerektirmeyen `using` ifade için aşağıdaki alternatif sözdizimini kullanabilirsiniz:

:::code language="csharp" source="snippets/usings.cs" id="SnippetModernUsing":::

## <a name="remarks"></a>Açıklamalar

<xref:System.IO.File>ve <xref:System.Drawing.Font> yönetilmeyen kaynaklara erişen yönetilen türlerin örnekleridir (Bu durumda dosya tutamaçları ve cihaz bağlamları). Birçok farklı türde yönetilmeyen kaynak ve bunları kapsülleyen sınıf kitaplığı türleri vardır. Bu tür türler <xref:System.IDisposable> arabirimini veya <xref:System.IAsyncDisposable> arabirimini gerçekleştirmelidir.

Bir `IDisposable` nesnenin yaşam süresi tek bir yöntemle sınırlı olduğunda, bu örneği `using` bildiriminde belirtmeniz ve oluşturmanız gerekir. `using` İfade, <xref:System.IDisposable.Dispose%2A> yöntemi nesnesi üzerinde doğru şekilde çağırır ve (daha önce gösterildiği gibi kullandığınızda), bu da nesnenin kendisinin kapsam <xref:System.IDisposable.Dispose%2A> dışına geçmesine neden olur ve çağrılır. `using` Blok içinde, nesne salt okunurdur ve değiştirilemez ya da yeniden atanamaz. Nesnesi yerine uygularsa `IAsyncDisposable` , `IDisposable` `using` <xref:System.IAsyncDisposable.DisposeAsync%2A> ifade öğesini ve `awaits` döndürülen <xref:System.Threading.Tasks.Task>öğesini çağırır.

Bu `using` <xref:System.IDisposable.Dispose%2A> ifade, `using` bloğunda bir özel <xref:System.IAsyncDisposable.DisposeAsync%2A>durum gerçekleşse bile (veya) çağrısı yapılmasını sağlar. Nesneyi bir `try` bloğun içine yerleştirerek ve sonra da (veya <xref:System.IDisposable.Dispose%2A> <xref:System.IAsyncDisposable.DisposeAsync%2A>) bir `finally` blokta çağırarak aynı sonucu elde edebilirsiniz; Aslında, `using` deyimin derleyici tarafından çevrilme yöntemi budur. Kod örneği, derleme zamanında aşağıdaki koda genişletilir (nesne için sınırlı kapsam oluşturmak için ek küme ayraçları aklınızda):

:::code language="csharp" source="snippets/usings.cs" id="SnippetTryFinallyExample":::

Daha yeni `using` ifade söz dizimi benzer bir koda dönüştürür. `try` Blok, değişkenin bildirildiği yerde açılır. `finally` Blok, genellikle bir yöntemin sonunda kapsayan bloğa yakın bir zamanda eklenir.

İfadesiyle ilgili `try` - daha fazla bilgi için bkz. [try-finally](try-finally.md) makalesi. `finally`

Aşağıdaki örnekte gösterildiği gibi, bir türün birden çok örneği tek `using` bir bildirimde bildirilebilecek. Tek bir ifadede birden çok değişken bildirdiğinizde örtük olarak`var`yazılmış değişkenleri () kullanamıyoruz.

:::code language="csharp" source="snippets/usings.cs" id="SnippetDeclareMultipleVariables":::

Aşağıdaki örnekte gösterildiği gibi, C# 8 ile sunulan yeni sözdizimini kullanarak aynı türdeki birden çok bildirimi birleştirebilirsiniz:

:::code language="csharp" source="snippets/usings.cs" id="SnippetModernMultipleVariables":::

Kaynak nesnesini örnekleyebilirsiniz ve sonra değişkeni `using` ifadeye geçirebilirsiniz, ancak bu en iyi yöntem değildir. Bu durumda, Denetim `using` bloğundan ayrıldıktan sonra nesne kapsamda kalır, büyük olasılıkla yönetilmeyen kaynaklarına erişemez. Diğer bir deyişle, artık tam olarak başlatılamaz. Nesneyi `using` bloğunun dışında kullanmaya çalışırsanız, bir özel durumun oluşturulması riskiyle karşılaşırsınız. Bu nedenle, `using` deyimindeki nesnenin örneğini oluşturmak ve kapsamını `using` bloğa sınırlamak daha iyidir.

:::code language="csharp" source="snippets/usings.cs" id="SnippetDeclareBeforeUsing":::

`IDisposable` Nesneleri elden atma hakkında daha fazla bilgi için bkz. [IDisposable uygulayan nesneleri kullanma](../../../standard/garbage-collection/using-objects.md).

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [using ifadesine](~/_csharplang/spec/statements.md#the-using-statement) bakın. Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# anahtar sözcükleri](index.md)
- [using Yönergesi](using-directive.md)
- [Çöp toplama](../../../standard/garbage-collection/index.md)
- [IDisposable uygulayan nesneleri kullanma](../../../standard/garbage-collection/using-objects.md)
- [IDisposable arabirimi](xref:System.IDisposable)
- [C# 8,0 ' de using deyimleri](~/_csharplang/proposals/csharp-8.0/using.md)
