---
title: Tarih ve saatlerle aritmetik işlemler gerçekleştirme
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- times [.NET Framework], arithmetic operations
- dates [.NET Framework], arithmetic operations
- time zones [.NET Framework], arithmetic operations
- arithmetic operations [.NET Framework], dates and times
- dates [.NET Framework], comparing
- DateTime structure, arithmetic operations
- DateTimeOffset structure, arithmetic operations
ms.assetid: 87c7ddf2-f15e-48af-8602-b3642237e6d0
ms.openlocfilehash: 0db0331620da8337930bfacf5d1bbd9913647afa
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344181"
---
# <a name="performing-arithmetic-operations-with-dates-and-times"></a>Tarih ve saatlerle aritmetik işlemler gerçekleştirme

Hem yapılar <xref:System.DateTime> hem <xref:System.DateTimeOffset> de yapılar kendi değerleri üzerinde aritmetik işlemler gerçekleştiren üyeler sağlasa da, aritmetik işlemlerin sonuçları çok farklıdır. Bu konu, bu farklılıkları inceler, tarih ve saat verilerindeki saat dilimi farkındalığı dereceleri ile ilgilidir ve tarih ve saat verilerini kullanarak tam saat dilimi farkında işlemleri nasıl gerçekleştireceklerini tartışır.

## <a name="comparisons-and-arithmetic-operations-with-datetime-values"></a>DateTime değerleri ile karşılaştırmalar ve aritmetik işlemler

Özellik, <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> yerel <xref:System.DateTimeKind> saati, Eşgüdümlü Evrensel Saati (UTC) veya belirtilmemiş bir saat dilimindeki saati temsil edip etmediğini belirtmek için tarih ve saate bir değer atanmasına izin verir. Ancak, bu sınırlı saat dilimi bilgileri, değerler üzerinde <xref:System.DateTimeKind> tarih ve saat aritmetiklerini karşılaştırırken veya gerçekleştirirken yoksayılır. Geçerli yerel saati geçerli UTC saati ile karşılaştıran aşağıdaki örnek, bunu göstermektedir.

[!code-csharp[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual2.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual2.vb#2)]

Yöntem, <xref:System.DateTime.CompareTo%28System.DateTime%29> yerel saatin UTC saatinden (veya daha az) daha erken olduğunu bildirir ve çıkarma işlemi UTC ile ABD Pasifik Standart Saat dilimindeki bir sistemin yerel saati arasındaki farkın yedi saat olduğunu gösterir. Ancak bu iki değer zaman içinde tek bir noktanın farklı gösterimlerini sağladığından, bu durumda zaman aralığının tamamen yerel saat diliminin UTC'den mahsup edilmesine atfedilebilir olduğu açıktır.

Daha genel olarak, <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> özellik karşılaştırma ve <xref:System.DateTime.Kind> aritmetik yöntemlerle döndürülen sonuçları etkilemez (zaman içinde iki özdeş noktanın karşılaştırılması nın gösterdiği gibi), ancak bu sonuçların yorumlanmasını etkileyebilir. Örnek:

- Özellikleri eşit olan <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> iki tarih ve saat değerlerinde gerçekleştirilen herhangi <xref:System.DateTimeKind> bir aritmetik işlemin sonucu, iki değer arasındaki gerçek zaman aralığını yansıtır. Benzer şekilde, bu tür iki tarih ve saat değerlerinin karşılaştırılması, zaman arasındaki ilişkiyi doğru bir şekilde yansıtır.

- <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> Özellikleri farklı <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> özellik değerlerine sahip iki tarih <xref:System.DateTimeKind> ve saat değerlerinde olan iki tarih ve saat değerlerinde gerçekleştirilen herhangi bir aritmetik veya karşılaştırma işleminin sonucu, iki değer arasındaki saat farkını yansıtır.

- Yerel tarih ve saat değerlerindeki aritmetik veya karşılaştırma işlemleri belirli bir değerin belirsiz veya geçersiz olup olmadığını dikkate almaz ve yerel saat diliminin gün ışığına veya gün ışığından geçişinden kaynaklanan herhangi bir ayarlama kuralının etkisini dikkate almaz. zamandan tasarruf sağlar.

- UTC ile yerel saat arasındaki farkı karşılaştıran veya hesaplayan herhangi bir işlem, sonuç olarak yerel saat diliminin UTC'den mahsup edilene eşit bir zaman aralığı içerir.

- Belirtilmeyen bir saat ile UTC veya yerel saat arasındaki farkı karşılaştıran veya hesaplayan herhangi bir işlem basit saat süresini yansıtır. Saat dilimi farklılıkları dikkate alınmaz ve sonuç saat dilimi ayarlama kurallarının uygulanmasını yansıtmaz.

- İki tanımlanmamış saat arasındaki farkı karşılaştıran veya hesaplayan herhangi bir işlem, iki farklı saat dilimindeki saat arasındaki farkı yansıtan bilinmeyen bir aralık içerebilir.

Saat dilimi farklılıklarının tarih ve saat hesaplamalarını etkilemediği birçok senaryo vardır (bunlardan bazılarının tartışılması için bkz. [DateTime, DateTimeOffset, TimeSpan ve TimeZoneInfo arasında seçim](../../../docs/standard/datetime/choosing-between-datetime.md)yapma) veya tarih ve saat verilerinin bağlamının karşılaştırma veya aritmetik işlemlerin anlamını tanımladığı.

## <a name="comparisons-and-arithmetic-operations-with-datetimeoffset-values"></a>DateTimeOffset değerleri ile karşılaştırmalar ve aritmetik işlemler

Değer <xref:System.DateTimeOffset> yalnızca bir tarih ve saat değil, aynı zamanda UTC'ye göre bu tarih ve saati kesin olarak tanımlayan bir mahsup içerir. Bu, eşitliği <xref:System.DateTimeOffset> değerlerden biraz farklı tanımlamayı mümkün kılar. Değerler <xref:System.DateTime> aynı tarih ve saat değerine sahipse eşitken, <xref:System.DateTimeOffset> her ikisi de zaman içinde aynı noktaya başvuruyorsa değerler eşittir. Bu, <xref:System.DateTimeOffset> karşılaştırmalarda ve iki tarih ve saat arasındaki aralığı belirleyen çoğu aritmetik işlemde kullanıldığında değeri daha doğru ve yoruma daha az ihtiyaç duyar. Yerel ve UTC <xref:System.DateTimeOffset> <xref:System.DateTimeOffset> değerlerini karşılaştıran önceki örneğe eşdeğer olan aşağıdaki örnek, davranıştaki bu farkı göstermektedir.

[!code-csharp[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual3.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual3.vb#3)]

Bu <xref:System.DateTimeOffset.CompareTo%2A> örnekte, yöntem geçerli yerel saat ve geçerli UTC saateşit olduğunu <xref:System.DateTimeOffset.CompareTo(System.DateTimeOffset)> gösterir ve değerlerin çıkarma iki <xref:System.TimeSpan.Zero?displayProperty=nameWithType>kez arasındaki fark gösterir .

Tarih ve saat <xref:System.DateTimeOffset> aritmetiğinde değerleri kullanmanın <xref:System.DateTimeOffset> en önemli sınırlaması, değerlerin bir miktar zaman dilimi farkındalığına sahip olmasına rağmen, tam olarak zaman dilimi farkında olmamalarıdır. Değerin <xref:System.DateTimeOffset> mahsup değeri, bir <xref:System.DateTimeOffset> değişkene ilk atandığında UTC'den gelen bir saat diliminin mahsupını yansıtsa da, bundan sonraki zaman diliminden ilişkisi kesilir. Artık tanımlanabilir bir saatle doğrudan ilişkili olmadığından, tarih ve saat aralıklarının eklenmesi ve çıkarTı bir saat diliminin ayarlama kurallarını dikkate almaz.

Göstermek için, ABD Merkezi Standart Saat diliminde yaz saatine geçiş 02:00'de gerçekleşir. 9 Mart 2008 tarihinde. Bu, Saat 01:30'daki Merkezi Standart saate iki buçuk saatlik bir aralık eklenmesi anlamına gelir. 9 Mart 2008 tarihinde, bir tarih ve saat 5:00 üretmelidir. 9 Mart 2008 tarihinde. Ancak, aşağıdaki örnekte de görüldüğü gibi, eklemenin sonucu 04:00'tir. 9 Mart 2008 tarihinde. Bu işlemin sonucunun, ilgilendiğimiz saat diliminde (yani beklenen saat dilimi mahsulü ne kadar önemli değilse) zaman içinde doğru noktayı temsil ettiğini unutmayın.

[!code-csharp[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual4.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual4.vb#4)]

## <a name="arithmetic-operations-with-times-in-time-zones"></a>Saat dilimlerinde süreleri ile aritmetik işlemler

Sınıf, <xref:System.TimeZoneInfo> kezleri bir saat diliminden diğerine dönüştürdüklerinde ayarlamaları otomatik olarak uygulayan bir dizi dönüştürme yöntemi içerir. Bunlar aşağıdakileri içerir:

- Herhangi <xref:System.TimeZoneInfo.ConvertTime%2A> <xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A> iki saat dilimi arasındaki süreleri dönüştüren yöntemler.

- Belirli <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A> <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> bir saat dilimindeki zamanı UTC'ye dönüştüren veya UTC'yi belirli bir saat dilimindeki saate dönüştüren yöntemler.

Ayrıntılar için bkz: [Saat dilimleri arasındaki saatleri dönüştürme.](../../../docs/standard/datetime/converting-between-time-zones.md)

Sınıf, <xref:System.TimeZoneInfo> tarih ve saat aritmetiği uyguladığınız zaman ayarlama kurallarını otomatik olarak uygulayan yöntemler sağlamaz. Ancak, bunu bir saat dilimindeki saati UTC'ye dönüştürerek, aritmetik işlemi gerçekleştirerek ve ardından UTC'den saat dilimindeki saate dönüştürerek yapabilirsiniz. Ayrıntılar için [bkz: Tarih ve saat aritmetiğinde saat dilimlerini kullanın.](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md)

Örneğin, aşağıdaki kod, saat 02:00'ye iki buçuk saat eklenen önceki koda benzer. 9 Mart 2008 tarihinde. Ancak, tarih ve saat aritmetik gerçekleştirmeden önce Merkezi Standart saati UTC'ye dönüştürüp UTC'den sonucu Merkezi Standart saate dönüştürdüğü için, ortaya çıkan saat Merkezi Standart Saat Dilimi'nin gün ışığından yararlanmaya geçişini yansıtır Zaman.

[!code-csharp[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual5.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual5.vb#5)]

## <a name="see-also"></a>Ayrıca bkz.

- [Tarihler, saatler ve saat dilimleri](../../../docs/standard/datetime/index.md)
- [Nasıl yapılır: Tarih ve saat aritmetiğinde saat dilimlerini kullanma](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md)
