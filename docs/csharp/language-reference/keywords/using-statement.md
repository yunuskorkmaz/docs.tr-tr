---
description: using deyimleri-C# başvurusu
title: using deyimleri-C# başvurusu
ms.date: 05/29/2020
helpviewer_keywords:
- using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
ms.openlocfilehash: c7f1fc4b7e911bdec3bd38ae88aa39b7f1795300
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141939"
---
# <a name="using-statement-c-reference"></a>using deyimleri (C# Başvurusu)

Nesnelerin doğru kullanımını sağlayan uygun bir sözdizimi sağlar <xref:System.IDisposable> . C# 8,0 ' den başlayarak, `using` ifade nesnelerin doğru kullanımını sağlar <xref:System.IAsyncDisposable> .

## <a name="example"></a>Örnek

Aşağıdaki örnek, ifadesinin nasıl kullanılacağını göstermektedir `using` .

:::code language="csharp" source="snippets/usings.cs" id="SnippetFirstExample":::

C# 8,0 ' den başlayarak, `using` küme ayraçları gerektirmeyen ifade için aşağıdaki alternatif sözdizimini kullanabilirsiniz:

:::code language="csharp" source="snippets/usings.cs" id="SnippetModernUsing":::

## <a name="remarks"></a>Açıklamalar

<xref:System.IO.File> ve <xref:System.Drawing.Font> yönetilmeyen kaynaklara erişen yönetilen türlerin örnekleridir (Bu durumda dosya tutamaçları ve cihaz bağlamları). Birçok farklı türde yönetilmeyen kaynak ve bunları kapsülleyen sınıf kitaplığı türleri vardır. Bu tür türler <xref:System.IDisposable> arabirimini veya <xref:System.IAsyncDisposable> arabirimini gerçekleştirmelidir.

Bir nesnenin yaşam süresi `IDisposable` tek bir yöntemle sınırlı olduğunda, bu örneği bildiriminde belirtmeniz ve oluşturmanız gerekir `using` . `using`İfade, <xref:System.IDisposable.Dispose%2A> yöntemi nesnesi üzerinde doğru şekilde çağırır ve (daha önce gösterildiği gibi kullandığınızda), bu da nesnenin kendisinin kapsam dışına geçmesine neden olur ve <xref:System.IDisposable.Dispose%2A> çağrılır. Blok içinde `using` , nesne salt okunurdur ve değiştirilemez ya da yeniden atanamaz. Nesnesi yerine uygularsa, `IAsyncDisposable` `IDisposable` `using` ifade öğesini ve döndürülen öğesini çağırır <xref:System.IAsyncDisposable.DisposeAsync%2A> `awaits` <xref:System.Threading.Tasks.ValueTask> . Hakkında daha fazla bilgi için <xref:System.IAsyncDisposable> bkz. [DisposeAsync yöntemi uygulama](../../../standard/garbage-collection/implementing-disposeasync.md).

`using`Bu ifade, <xref:System.IDisposable.Dispose%2A> <xref:System.IAsyncDisposable.DisposeAsync%2A> bloğunda bir özel durum gerçekleşse bile (veya) çağrısı yapılmasını sağlar `using` . Nesneyi bir blok içine yerleştirerek `try` ve sonra da <xref:System.IDisposable.Dispose%2A> (veya) bir blokta çağırarak aynı sonucu elde edebilirsiniz <xref:System.IAsyncDisposable.DisposeAsync%2A> `finally` ; aslında, bu, `using` deyimin derleyici tarafından çevrilme yöntemi olur. Kod örneği, derleme zamanında aşağıdaki koda genişletilir (nesne için sınırlı kapsam oluşturmak için ek küme ayraçları aklınızda):

:::code language="csharp" source="snippets/usings.cs" id="SnippetTryFinallyExample":::

Daha yeni `using` ifade söz dizimi benzer bir koda dönüştürür. `try`Blok, değişkenin bildirildiği yerde açılır. `finally`Blok, genellikle bir yöntemin sonunda kapsayan bloğa yakın bir zamanda eklenir.

İfadesiyle ilgili daha fazla bilgi için `try` - `finally` bkz. [try-finally](try-finally.md) makalesi.

Aşağıdaki örnekte gösterildiği gibi, bir türün birden çok örneği tek bir bildirimde bildirilebilecek `using` . `var`Tek bir ifadede birden çok değişken bildirdiğinizde örtük olarak yazılmış değişkenleri () kullanamıyoruz.

:::code language="csharp" source="snippets/usings.cs" id="SnippetDeclareMultipleVariables":::

Aşağıdaki örnekte gösterildiği gibi, C# 8 ile sunulan yeni sözdizimini kullanarak aynı türdeki birden çok bildirimi birleştirebilirsiniz:

:::code language="csharp" source="snippets/usings.cs" id="SnippetModernMultipleVariables":::

Kaynak nesnesini örnekleyebilirsiniz ve sonra değişkeni `using` ifadeye geçirebilirsiniz, ancak bu en iyi yöntem değildir. Bu durumda, denetim bloğundan ayrıldıktan sonra `using` nesne kapsamda kalır, büyük olasılıkla yönetilmeyen kaynaklarına erişemez. Diğer bir deyişle, artık tam olarak başlatılamaz. Nesneyi bloğunun dışında kullanmaya çalışırsanız `using` , bir özel durumun oluşturulması riskiyle karşılaşırsınız. Bu nedenle, deyimindeki nesnenin örneğini oluşturmak `using` ve kapsamını bloğa sınırlamak daha iyidir `using` .

:::code language="csharp" source="snippets/usings.cs" id="SnippetDeclareBeforeUsing":::

Nesneleri elden atma hakkında daha fazla bilgi için `IDisposable` bkz. [IDisposable uygulayan nesneleri kullanma](../../../standard/garbage-collection/using-objects.md).

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
