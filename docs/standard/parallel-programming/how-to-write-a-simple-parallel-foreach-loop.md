---
title: Parallel. ForEach kullanarak basit bir paralel program yazın
description: Bu makalede, .NET 'te veri paralelliğini nasıl etkinleştireceğinizi öğrenin. Herhangi bir IEnumerable veya IEnumerable veri kaynağı üzerinde bir Parallel. ForEach Döngüsü yazın <T> .
ms.date: 02/23/2021
dev_langs:
- csharp
- vb
helpviewer_keywords:
- foreach, parallel version
- parallel programming, foreach
ms.assetid: cb5fab92-1c19-499e-ae91-8b7525dd875f
ms.openlocfilehash: 50c60d730fbf930ea369b014e2f8f971e9c1f239
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102106689"
---
# <a name="how-to-write-a-simple-parallelforeach-loop"></a>Nasıl yapılır: basit bir Parallel. ForEach Döngüsü Yazma

Bu örnek, <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> herhangi bir <xref:System.Collections.IEnumerable?displayProperty=nameWithType> veya veri kaynağı üzerinde veri paralelliğini etkinleştirmek için döngüsünün nasıl kullanılacağını gösterir <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> .

> [!NOTE]
> Bu belgede, PLıNQ içinde temsilciler tanımlamak için lambda ifadeleri kullanılmaktadır. C# veya Visual Basic lambda ifadeleriyle ilgili bilgi sahibi değilseniz bkz. [PLıNQ ve TPL Içindeki lambda ifadeleri](lambda-expressions-in-plinq-and-tpl.md).

## <a name="example"></a>Örnek

Bu örnek, <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> CPU yoğun işlemlerini gösterir. Örneği çalıştırdığınızda rastgele 2.000.000 sayı üretir ve asal sayılara filtre uygulamayı dener. İlk durum, bir döngü aracılığıyla koleksiyonu yineler `for` . İkinci durum, ile koleksiyonun üzerinde yinelenir <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> . Her yineleme tarafından alınan sonuç süresi, uygulama tamamlandığında görüntülenir.

[!code-csharp[TPL_Parallel#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleforeach.cs#03)]
[!code-vb[TPL_Parallel#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleforeach.vb#03)]

<xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>Döngü bir döngü gibi çalışmaktadır <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> . Döngü, kaynak koleksiyonu bölümler ve sistem ortamına göre birden çok iş parçacığında çalışmayı zamanlar. Sistemde daha fazla işlemci varsa, paralel yöntem daha hızlı çalışır. Bazı kaynak koleksiyonlarında, kaynağın boyutuna ve döngünün gerçekleştirdiği iş türüne bağlı olarak sıralı bir döngü daha hızlı olabilir. Performans hakkında daha fazla bilgi için bkz. [veri ve görev paralelliği Içindeki olası](potential-pitfalls-in-data-and-task-parallelism.md)bilgiler.

Paralel döngüler hakkında daha fazla bilgi için bkz. [nasıl yapılır: basit bir Parallel. for döngüsü yazma](how-to-write-a-simple-parallel-for-loop.md).

<xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>Genel olmayan bir koleksiyonla birlikte kullanmak için, <xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType> Aşağıdaki örnekte gösterildiği gibi, koleksiyonu genel bir koleksiyona dönüştürmek için genişletme yöntemini kullanabilirsiniz:

[!code-csharp[TPL_Parallel#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/nongeneric.cs#07)]
[!code-vb[TPL_Parallel#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/nongeneric.vb#07)]

Ayrıca, veri kaynaklarının işlenmesini paralel hale getirmek için paralel LINQ (PLıNQ) kullanabilirsiniz <xref:System.Collections.Generic.IEnumerable%601> . PLıNQ, döngü davranışını ifade etmek için bildirime dayalı sorgu söz dizimi kullanmanıza olanak sağlar. Daha fazla bilgi için bkz. [Parallel LINQ (PLıNQ)](introduction-to-plinq.md).

## <a name="compile-and-run-the-code"></a>Kodu derleyin ve çalıştırın

Kodu, .NET Framework için bir konsol uygulaması olarak veya .NET Core için bir konsol uygulaması olarak derleyebilirsiniz.

Visual Studio 'da, Windows Masaüstü ve .NET Core için Visual Basic ve C# konsol uygulaması şablonları vardır.

Komut satırından .NET Core CLI komutlarını (örneğin, `dotnet new console` veya `dotnet new console -lang vb` ) kullanabilir ya da dosyayı oluşturabilir ve komut satırı derleyicisini .NET Framework bir uygulama için kullanabilirsiniz.

Bir .NET Core konsol uygulamasını komut satırından çalıştırmak için `dotnet run` uygulamanızı içeren klasörden kullanın.

Konsol uygulamanızı Visual Studio 'dan çalıştırmak için **F5**'e basın.

## <a name="see-also"></a>Ayrıca bkz.

- [Veri paralelliği](data-parallelism-task-parallel-library.md)
- [Paralel programlama](index.md)
- [Paralel LINQ (PLINQ)](introduction-to-plinq.md)
