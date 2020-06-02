---
title: Windows üzerinde büyük nesne yığını (LOH)
description: Bu makalede büyük nesneler, .NET atık toplayıcısı tarafından nasıl yönetildiği ve büyük nesneleri kullanmanın performans etkileri anlatılmaktadır.
ms.date: 05/02/2018
helpviewer_keywords:
- large object heap (LOH)"
- LOH
- garbage collection, large object heap
- GC [.NET ], large object heap
ms.openlocfilehash: 87105acbd43eb8eda0daa00c65ca0635f5e1cc74
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286034"
---
# <a name="the-large-object-heap-on-windows-systems"></a>Windows sistemlerinde büyük nesne yığını

.NET çöp toplayıcı (GC), nesneleri küçük ve büyük nesnelere böler. Bir nesne büyükse, bazı öznitelikleri nesnenin küçük olmasına göre daha önemli hale gelir. Örneğin, bunu sıkıştırmak, &mdash; başka bir yere yığın üzerine kopyalamak &mdash; pahalı olabilir. Bu nedenle, atık toplayıcı büyük nesne yığınına (LOH) büyük nesneler koyar. Bu makalede, bir nesneyi büyük bir nesne olarak niteleyen, büyük nesnelerin nasıl toplandığı ve büyük nesnelerin ne tür performans etkilerine yönelik olduğunu ele alınmaktadır.

> [!IMPORTANT]
> Bu makalede, yalnızca Windows sistemlerinde çalışan .NET Framework ve .NET Core 'daki büyük nesne yığını ele alınmaktadır. Diğer platformlarda .NET uygulamalarında çalışan LOH 'yi kapsamaz.

## <a name="how-an-object-ends-up-on-the-loh"></a>Bir nesne LOH üzerinde nasıl sona eriyor

Bir nesne boyut olarak 85.000 bayttan büyükse veya eşitse, büyük bir nesne olarak kabul edilir. Bu sayı performans ayarlaması tarafından belirlendi. Bir nesne ayırma isteği 85.000 veya daha fazla bayt için olduğunda, çalışma zamanı onu büyük nesne yığınında ayırır.

Bunun ne anlama geldiğini anlamak için, atık toplayıcıyla ilgili bazı temelleri incelemek yararlı olur.

Çöp toplayıcı, bir genel toplayıcı. Üç nesle sahiptir: nesil 0, 1. nesil ve 2. nesil. 3 nesin olmasının nedeni, iyi ayarlanmış bir uygulamada, çoğu nesne gen0 ' de zar. Örneğin, bir sunucu uygulamasında her bir istekle ilişkili ayırmalar istek bittikten sonra zar almalıdır. Uçuş aşamasında ayırma istekleri bunu gen1 ve zar alacak şekilde yapar. Temelde, Gen1 küçük nesne alanlarıyla uzun süreli nesne alanı arasında bir arabellek işlevi görür.

Küçük nesneler her zaman 0. kuşak olarak ayrılır ve yaşam süresine bağlı olarak 1. veya generation2 sürümüne yükseltilebilir. Büyük nesneler her zaman 2. nesil olarak ayrılır.

Büyük nesneler yalnızca 2. nesil bir koleksiyon sırasında toplandıklarından 2. nesil için geçerlidir. Bir oluşturma toplandığında, tüm küçük oluşturma öğeleri de toplanır. Örneğin, 1. nesil bir GC gerçekleştiğinde hem 1. kuşak hem de 0 toplanır. 2. nesil GC gerçekleştiğinde, tüm yığın toplanır. Bu nedenle, 2. nesil GC 'nin *tam GC*olarak da denir. Bu makale, tam GC yerine 2. nesil GC 'ye başvurur, ancak şartlar aynı şekilde değiştirilebilir.

Nesiller, GC yığınının mantıksal bir görünümünü sağlar. Fiziksel olarak, nesneler yönetilen yığın kesimlerinde bulunurlar. *Yönetilen bir yığın segmenti* , yönetilen kod adına [VIRTUALALLOC işlevini](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) çağırarak GC 'nin işletim sisteminden ayrılmış bir bellek öbektir. CLR yüklendiğinde, GC iki başlangıç yığın kesimini ayırır: biri küçük nesneler (küçük nesne yığını veya SOH) için, diğeri ise büyük nesneler için (büyük nesne yığını).

Bu yönetilen yığın kesimlerinde yönetilen nesneler yerleştirilerek, ayırma istekleri karşılanır. Nesne 85.000 bayttan küçükse, SOH için kesime konur; Aksi takdirde, bir LOH segmentine konur. Bölümler, üzerinde daha fazla nesne ayrıldığından (daha küçük öbeklerde) kaydedilir.
SOH için, GC 'yi sürdüren nesneler bir sonraki oluşturmaya yükseltilir. Nesil 0 koleksiyonunu etkileyen nesneler artık 1. kuşak nesneler olarak kabul edilir. Ancak, en eski üretimi sürdüren nesneler hala en eski nesil olarak kabul edilir. Diğer bir deyişle 2. nesil, 2. nesil nesnelerdir. LOH 'den ve, LOH nesneleri (Gen2 ile toplanan).

Kullanıcı kodu yalnızca nesil 0 (küçük nesneler) veya LOH (büyük nesneler) halinde ayrılabilir. Yalnızca GC, 1. nesil nesneleri "ayırabilir" (nesil 0 ' dan kalan VNET 'ler yükselterek) ve 2. nesil (nesilleri 1 ve 2 ' den yükseltmek için).

Bir çöp toplama tetiklendiğinde, GC canlı nesneler aracılığıyla izler ve bunları sıkıştırır. Ancak, sıkıştırma pahalı olduğundan *, GC,* Loh; büyük nesne ayırma isteklerini karşılamak için daha sonra yeniden kullanılabilen, ölü nesnelerden ücretsiz bir liste oluşturur. Bitişik ölü nesneler tek bir ücretsiz nesne içinde yapılır.

.NET Core ve .NET Framework (.NET Framework 4.5.1 ile başlayarak), <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode?displayProperty=nameWithType> kullanıcıların bir sonraki tam engelleme GC sırasında LOH 'nin sıkıştırılması gerektiğini belirtmesini sağlayan özelliği içerir. Daha sonra .NET, LOH 'yi otomatik olarak sıkıştırmak isteyebilir. Bu, büyük nesneler tahsis ederseniz ve bunların taşınmadığından emin olmak istiyorsanız onları hala sabitlediğinizden emin olmak anlamına gelir.

Şekil 1 ' de, GC formlarının ilk nesil 0 GC 'den sonra 1 ' in oluşturduğu ve `Obj1` `Obj3` ölü ve ilk nesıl 1 GC sonrasında 2 `Obj2` . nesil ve kapalı olduğu bir senaryo gösterilir `Obj5` . Bu ve aşağıdaki rakamların yalnızca çizim amaçlarıyla olduğunu unutmayın; yığın üzerinde ne olacağını daha iyi göstermek için çok az nesne içerirler. Gerçekte, genellikle bir GC 'ye dahil birçok nesne daha vardır.

![Şekil 1: bir gen 0 GC ve Gen 1 GC](media/loh/loh-figure-1.jpg)\
Şekil 1: nesil 0 ve 1. nesil GC.

Şekil 2 ' nin, ve ölü olduğunu belirten 2. nesil GC sonrasında `Obj1` `Obj2` , GC 'nin, `Obj1` ve `Obj2` için bir ayırma isteğini karşılamak için kullanılan bellek içi boş alan `Obj4` olduğunu gösterir. Son nesneden sonra, `Obj3` segmentin sonuna kadar olan boşluk, ayırma isteklerini karşılamak için de kullanılabilir.

![Şekil 2: bir gen 2 GC 'den sonra](media/loh/loh-figure-2.jpg)\
Şekil 2:2. nesil GC 'den sonra

Büyük nesne ayırma isteklerini barındırmak için yeterli boş alan yoksa, GC ilk olarak IŞLETIM sisteminden daha fazla kesim edinmeyi dener. Bu başarısız olursa, biraz alan boşaltmayı umuyoruz 2. nesil GC 'yi tetikler.

1. nesil veya 2. nesil GC sırasında, atık toplayıcı, [VirtualFree işlevini](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree)çağırarak işletim sistemlerinde canlı nesneleri olmayan kesimleri serbest bırakır. Segmentin sonuna kadar olan son canlı nesneden sonra gelen boşluk, (gen0/Gen1 Live 'un, uygulamanızın doğru bir şekilde ayrıldığı için çöp toplayıcısının bir süre önce tutulması durumunda) yürütüldüğünden çalışır. Ve boş alanlar sıfırlansa da, bu da işletim sisteminin verileri diske geri yazmasına gerek olmadığı anlamına gelir.

LOH yalnızca 2. kuşak sırasında toplandığından, LOH segmenti yalnızca bu tür bir GC sırasında serbest bırakılabilirler. Şekil 3 ' te, çöp toplayıcı 'nın bir kesimi (segment 2) işletim sistemine yeniden yayınlayıp kalan kesimlerde daha fazla alan yürütmelerinin bulunduğu bir senaryo gösterilmektedir. Büyük nesne ayırma isteklerini karşılamak için segmentin sonunda, ayrılan alan seçimini kullanması gerekiyorsa, belleği yeniden kaydeder. (COMMIT/COMMIT hakkında bir açıklama için bkz. [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc)belgeleri.

![Şekil 3: Gen 2 GC sonrasında LOH](media/loh/loh-figure-3.jpg)\
Şekil 3:2. nesil GC sonrasında LOH

## <a name="when-is-a-large-object-collected"></a>Büyük bir nesne ne zaman toplanır?

Genel olarak, aşağıdaki üç koşuldan biri altında bir GC oluşur:

- Ayırma, 1. kuşak veya büyük nesne eşiğini aşıyor.

  Eşik, oluşturma özelliğinin bir özelliğidir. Atık toplayıcı nesneleri içine ayırdığı zaman oluşturma için bir eşik ayarlanır. Eşik aşıldığında, bu Neste bir GC tetiklenir. Küçük veya büyük nesneler ayırdığınızda, 1. nesil ve LOH 'nin eşiklerini sırasıyla kullanın. Çöp toplayıcı 1. ve 2. kuşak olarak tahsis edildiğinde, eşiklerini kullanır. Bu eşikler program çalışırken dinamik olarak ayarlanır.

  Bu tipik durumdur; çoğu GCs, yönetilen yığında ayırmalar nedeniyle gerçekleşir.

- <xref:System.GC.Collect%2A?displayProperty=nameWithType>Yöntemi çağrılır.

  Parametresiz <xref:System.GC.Collect?displayProperty=nameWithType> yöntemi çağrılırsa veya başka bir aşırı yükleme <xref:System.GC.MaxGeneration?displayProperty=nameWithType> bir bağımsız değişken olarak GEÇIRILIYORSA Loh, yönetilen yığının geri kalanı ile birlikte toplanır.

- Sistem düşük bellek durumunda.

  Bu durum, çöp toplayıcı IŞLETIM sisteminden yüksek bellek bildirimi aldığında oluşur. 2. nesil GC 'yi yapan çöp toplayıcı 'nın üretken olması, bir tane tetikler.

## <a name="loh-performance-implications"></a>LOH performansı etkileri

Büyük nesne yığını üzerindeki ayırmaların performansı aşağıdaki yollarla etkiler.

- Ayırma maliyeti.

  CLR, verdiği her yeni nesne için belleğin temizlenme garantisi verir. Bu, büyük bir nesnenin ayırma maliyetinin, bellek temizleme (bir GC tetiklediği durumlar dışında) tarafından tamamen eşit olduğu anlamına gelir. Bir bayt temizlemek için 2 döngü alırsa, en küçük büyük nesneyi temizlemek için 170.000 döngü sürer. Bir 2GHz makinesindeki 16. nesnenin belleğinin temizlenmesi yaklaşık 16 MS sürer. Bu çok büyük bir maliyettir.

- Toplama maliyeti.

  LOH ve 2. nesil birlikte toplandığından, birinin eşiği aşılırsa 2. nesil bir koleksiyon tetiklenir. 2. nesil bir koleksiyon, LOH nedeniyle tetikleniyorsa 2. nesil GC 'den sonra çok daha küçük olmamalıdır. 2. nesil üzerinde çok fazla veri yoksa, bu en az etkiye sahiptir. Ancak 2. nesil büyükse, çok sayıda nesil 2 GB tetiklendiğinde performans sorunlarına neden olabilir. Birçok büyük nesne çok geçici olarak ayrılmışsa ve büyük bir SOH varsa, GCs 'yi çok fazla zaman harcamış olursunuz. Ayrıca, gerçekten büyük nesneleri ayırmayı ve bunlara izin vermek istiyorsanız ayırma maliyeti gerçekten eklenebilir.

- Başvuru türlerine sahip dizi öğeleri.

  LOH üzerindeki çok büyük nesneler genellikle dizilerdir (gerçekten büyük bir örnek nesnesi olması çok nadir). Bir dizinin öğeleri başvuru açısından zengin ise, öğeler referans açısından zengin değilse, mevcut olmayan bir maliyet doğurur. Öğe herhangi bir başvuru içermiyorsa, çöp toplayıcının dizi içinde herhangi bir diziye gitmesi gerekmez. Örneğin, düğümleri bir ikili ağaçta depolamak için bir dizi kullanırsanız, bunu uygulamanın bir yolu, bir düğümün sağ ve sol düğümüne gerçek düğümlere başvurmanız gerekir:

  ```csharp
  class Node
  {
     Data d;
     Node left;
     Node right;
  };

  Node[] binary_tr = new Node [num_nodes];
  ```

  `num_nodes`Büyükse, çöp toplayıcı her öğe için en az iki başvuruya gitmenize ihtiyaç duyuyor. Bir alternatif yaklaşım, sağ ve sol düğümlerin dizinini depooluşturmaktır:

  ```csharp
  class Node
  {
     Data d;
     uint left_index;
     uint right_index;
  } ;
  ```

  Sol düğümün verilerini olarak `left.d` başvurmak yerine, buna olarak başvurabilirsiniz `binary_tr[left_index].d` . Çöp toplayıcı 'nın sol ve sağ düğüm için herhangi bir başvuruya bakmasına gerek yoktur.

Üç faktörden, ilk ikisi genellikle üçte daha önemdir. Bu nedenle, geçici olanları ayırmak yerine yeniden kullandığınız büyük nesnelerin bir havuzunu ayırmanız önerilir.

## <a name="collect-performance-data-for-the-loh"></a>LOH için performans verilerini toplama

Belirli bir alan için performans verilerini toplamadan önce, aşağıdakileri yapmış olmanız gerekir:

1. Bu alana baktığınız için kanıt bulundu.

2. Gördüğünüz performans sorununu açıklayacak herhangi bir şeyi bulmaksızın, bildiğiniz diğer alanlardan haberdar olabilirsiniz.

Bellek ve CPU temelleri hakkında daha fazla bilgi için [bir çözüm bulmaya çalışmadan önce blogda sorunu anlama](https://devblogs.microsoft.com/dotnet/understand-the-problem-before-you-try-to-find-a-solution/) bölümüne bakın.

LOH performansı üzerinde veri toplamak için aşağıdaki araçları kullanabilirsiniz:

- [.NET CLR bellek performansı sayaçları](#net-clr-memory-performance-counters)

- [ETW olayları](#etw-events)

- [Bir hata ayıklayıcı](#a-debugger)

### <a name="net-clr-memory-performance-counters"></a>.NET CLR bellek performansı sayaçları

Bu performans sayaçları genellikle performans sorunlarını araştırmaya yönelik iyi bir ilk adımdır (ancak [ETW olaylarını](#etw-events)kullanmanızı öneririz). Şekil 4 ' ün gösterdiği gibi, istediğiniz sayaçları ekleyerek performans Izleyicisini yapılandırırsınız. LOH ile ilgili olanlar şunlardır:

- **Gen 2 toplamaları**

   İşlem başladıktan sonra 2. nesil oluşturma işleminin kaç kez gerçekleştiğini görüntüler. Sayaç, 2. kuşak koleksiyonun (tam çöp toplama da denir) sonunda artırılır. Bu sayaç, son gözlemlenen değeri görüntüler.

- **Büyük nesne yığın boyutu**

   LOH 'nin boş alanı da dahil olmak üzere geçerli boyutunu bayt cinsinden görüntüler. Bu sayaç her ayırmada değil çöp toplamanın sonunda güncelleştirilir.

Performans sayaçlarından bakmak için yaygın olarak kullanılan bir yöntem, performans Izleyicisine (Perfmon. exe) sahiptir. İlgilendiğiniz işlemlere yönelik ilginç sayaç eklemek için "Sayaç Ekle" öğesini kullanın. Şekil 4 ' ün gösterdiği gibi, performans sayacı verilerini bir günlük dosyasına kaydedebilirsiniz:

![Performans sayaçlarını eklemeyi gösteren ekran görüntüsü.](media/large-object-heap/add-performance-counter.png)
Şekil 4:2. nesil GC sonrasında LOH

Performans sayaçları programlama yoluyla da sorgulanabilir. Birçok kişi bu şekilde rutin test sürecinin bir parçası olarak toplanır. Sıradan olmayan değerlere sahip sayaçları fark ettikleri zaman, araştırmaya yardımcı olacak daha ayrıntılı veriler almak için başka bir yöntem kullanır.

> [!NOTE]
> ETW çok daha zengin bilgi sağladığından performans sayaçları yerine ETW olaylarını kullanmanızı öneririz.

### <a name="etw-events"></a>ETW olayları

Çöp toplayıcı, yığının ne yaptığını ve nedenini anlamanıza yardımcı olmak için zengin bir ETW olayları kümesi sağlar. Aşağıdaki blog gönderileri ETW ile GC olaylarını nasıl toplayacağınızı ve anlayacağını göstermektedir:

- [GC ETW olayları-1](https://devblogs.microsoft.com/dotnet/gc-etw-events-1/)

- [GC ETW olayları-2](https://devblogs.microsoft.com/dotnet/gc-etw-events-2/)

- [GC ETW olayları-3](https://devblogs.microsoft.com/dotnet/gc-etw-events-3/)

- [GC ETW olayları-4](https://devblogs.microsoft.com/dotnet/gc-etw-events-4/)

Geçici LOH ayırmaları nedeniyle oluşan aşırı nesil 2 GB 'yi belirlemek için, GCs için tetikleyici nedeni sütununa bakın. Yalnızca geçici büyük nesneleri ayıran basit bir test için aşağıdaki [PerfView](https://www.microsoft.com/download/details.aspx?id=28567) komut SATıRı ile ETW olayları hakkında bilgi toplayabilirsiniz:

```console
perfview /GCCollectOnly /AcceptEULA /nogui collect
```

Sonuç şuna benzer:

![PerfView 'da ETW olaylarını gösteren ekran görüntüsü.](media/large-object-heap/event-tracing-windows-perfview.png)
Şekil 5: PerfView kullanılarak gösterilen ETW olayları

Görebileceğiniz gibi, tüm GCs 'ler 2 GB kuşak ve hepsi AllocLarge tarafından tetiklendikleri için, büyük bir nesnenin tahsis edilen bu GC 'yi tetiklediği anlamına gelir. **Loh kalan değer oranı%** sütunu %1 diyor olduğundan bu ayırmaların geçici olduğunu biliyoruz.

Bu büyük nesneleri kimin ayıryacağını söyleyen ek ETW olayları toplayabilirsiniz. Aşağıdaki komut satırı:

```console
perfview /GCOnly /AcceptEULA /nogui collect
```

ayırmaların yaklaşık olarak her 100.000 değerinde harekete geçen bir allocationtick olayı toplar. Diğer bir deyişle, büyük bir nesne ayrıldığında her seferinde bir olay tetiklenir. Daha sonra, büyük nesneleri ayrılan çağrı yığınlarını gösteren GC yığın ayırma görünümlerinden birine bakabilirsiniz:

![Çöp toplayıcı yığın görünümünü gösteren ekran görüntüsü.](media/large-object-heap/garbage-collector-heap.png)
Şekil 6: GC yığın ayırma görünümü

Gördüğünüz gibi, bu çok basit bir sınamadır ve yalnızca kendi yönteminden büyük nesneleri ayırır `Main` .

### <a name="a-debugger"></a>Bir hata ayıklayıcı

Bir bellek dökümünlükleriniz varsa ve hangi nesnelerin gerçekten LOH üzerinde olduğuna bakmanız gerekiyorsa, .NET tarafından sunulan [sos hata ayıklayıcı uzantısını](../../framework/tools/sos-dll-sos-debugging-extension.md) kullanabilirsiniz.

> [!NOTE]
> Bu bölümde bahsedilen hata ayıklama komutları [Windows hata ayıklayıcıları](https://www.microsoft.com/whdc/devtools/debugging/default.mspx)için geçerlidir.

Aşağıda, LOH 'yi analiz etmenin örnek çıktısı gösterilmektedir:

```console
0:003> .loadby sos mscorwks
0:003> !eeheap -gc
Number of GC Heaps: 1
generation 0 starts at 0x013e35ec
sdgeneration 1 starts at 0x013e1b6c
generation 2 starts at 0x013e1000
ephemeral segment allocation context: none
segment   begin allocated     size
0018f2d0 790d5588 790f4b38 0x0001f5b0(128432)
013e0000 013e1000 013e35f8 0x000025f8(9720)
Large object heap starts at 0x023e1000
segment   begin allocated     size
023e0000 023e1000 033db630 0x00ffa630(16754224)
033e0000 033e1000 043cdf98 0x00fecf98(16699288)
043e0000 043e1000 05368b58 0x00f87b58(16284504)
Total Size 0x2f90cc8(49876168)
------------------------------
GC Heap Size 0x2f90cc8(49876168)
0:003> !dumpheap -stat 023e1000 033db630
total 133 objects
Statistics:
MT   Count   TotalSize Class Name
001521d0       66     2081792     Free
7912273c       63     6663696 System.Byte[]
7912254c       4     8008736 System.Object[]
Total 133 objects
```

LOH yığın boyutu (16.754.224 + 16.699.288 + 16.284.504) = 49.738.016 bayttır. /Mm E1000 ve 033db630 adresleri arasında, 8.008.736 bayt bir nesne dizisi tarafından kullanılıyor <xref:System.Object?displayProperty=nameWithType> , 6.663.696 bayt bir nesne dizisi tarafından kullanılıyor <xref:System.Byte?displayProperty=nameWithType> ve 2.081.792 bayt boş alana göre yer kaplar.

Bazen hata ayıklayıcı, LOH 'nin toplam boyutunun 85.000 bayttan daha az olduğunu gösterir. Bu durum, çalışma zamanının, büyük bir nesneden küçük bazı nesneleri ayırmak için LOH 'yi kullanması nedeniyle oluşur.

LOH sıkıştırmadığından, bazen LOH 'nin parçalanma kaynağı olduğu düşünülebilir. Parçalanma anlamı:

- Yönetilen yığının, yönetilen nesneler arasındaki boş alan miktarına göre belirtilen parçalanması. SoS 'de, `!dumpheap –type Free` komut yönetilen nesneler arasındaki boş alan miktarını görüntüler.

- Olarak işaretlenen bellek olan sanal bellek (VM) adres alanının parçalanması `MEM_FREE` . WinDbg 'de çeşitli hata ayıklayıcı komutlarını kullanarak edinebilirsiniz.

   Aşağıdaki örnek, VM alanındaki parçalanmayı göstermektedir:

   ```console
   0:000> !address
   00000000 : 00000000 - 00010000
   Type     00000000
   Protect 00000001 PAGE_NOACCESS
   State   00010000 MEM_FREE
   Usage   RegionUsageFree
   00010000 : 00010000 - 00002000
   Type     00020000 MEM_PRIVATE
   Protect 00000004 PAGE_READWRITE
   State   00001000 MEM_COMMIT
   Usage   RegionUsageEnvironmentBlock
   00012000 : 00012000 - 0000e000
   Type     00000000
   Protect 00000001 PAGE_NOACCESS
   State   00010000 MEM_FREE
   Usage   RegionUsageFree
   … [omitted]
   -------------------- Usage SUMMARY --------------------------
   TotSize (     KB)   Pct(Tots) Pct(Busy)   Usage
   701000 (   7172) : 00.34%   20.69%   : RegionUsageIsVAD
   7de15000 ( 2062420) : 98.35%   00.00%   : RegionUsageFree
   1452000 (   20808) : 00.99%   60.02%   : RegionUsageImage
   300000 (   3072) : 00.15%   08.86%   : RegionUsageStack
   3000 (     12) : 00.00%   00.03%   : RegionUsageTeb
   381000 (   3588) : 00.17%   10.35%   : RegionUsageHeap
   0 (       0) : 00.00%   00.00%   : RegionUsagePageHeap
   1000 (       4) : 00.00%   00.01%   : RegionUsagePeb
   1000 (       4) : 00.00%   00.01%   : RegionUsageProcessParametrs
   2000 (       8) : 00.00%   00.02%   : RegionUsageEnvironmentBlock
   Tot: 7fff0000 (2097088 KB) Busy: 021db000 (34668 KB)

   -------------------- Type SUMMARY --------------------------
   TotSize (     KB)   Pct(Tots) Usage
   7de15000 ( 2062420) : 98.35%   : <free>
   1452000 (   20808) : 00.99%   : MEM_IMAGE
   69f000 (   6780) : 00.32%   : MEM_MAPPED
   6ea000 (   7080) : 00.34%   : MEM_PRIVATE

   -------------------- State SUMMARY --------------------------
   TotSize (     KB)   Pct(Tots) Usage
   1a58000 (   26976) : 01.29%   : MEM_COMMIT
   7de15000 ( 2062420) : 98.35%   : MEM_FREE
   783000 (   7692) : 00.37%   : MEM_RESERVE

   Largest free region: Base 01432000 - Size 707ee000 (1843128 KB)
   ```

Atık toplayıcısının genellikle IŞLETIM sisteminden yeni yönetilen yığın kesimleri elde etmek ve yeniden işletim sistemine tekrar serbest bırakmak için çöp toplayıcı 'nın neden olduğu geçici büyük nesnelerden kaynaklanan VM parçalanması ' nı görmek daha yaygındır.

LOH 'nin VM [parçalanmaya](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree) neden olup olmadığını doğrulamak Için, [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) üzerinde bir kesme noktası ayarlayabilir ve onları kimlerin çağırabildiğini görebilirsiniz. Örneğin, IŞLETIM sisteminden 8MBB 'den büyük sanal bellek öbekleri ayırmaya çalışan kişileri görmek için şöyle bir kesme noktası ayarlayabilirsiniz:

```console
bp kernel32!virtualalloc "j (dwo(@esp+8)>800000) 'kb';'g'"
```

Bu komut, hata ayıklayıcıya kesilir ve çağrı yığınını yalnızca, [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) 'tan daha büyük bir ayırma boyutuyla (0x800000) çağrıldığında çağrı yığınını gösterir.

CLR 2,0, parçaların (büyük ve küçük nesne yığınlarıyla birlikte) sıklıkla alındığı ve yayımlandığı senaryolar için yararlı olabilecek *VM hoarding* adlı bir özellik ekledi. VM hoarding belirtmek için `STARTUP_HOARD_GC_VM` barındırma API 'si aracılığıyla çağrılan bir başlangıç bayrağı belirtirsiniz. CLR, boş kesimleri yeniden işletim sistemine serbest bırakmak yerine bu kesimlerdeki belleği kaydeder ve bir bekleme listesine koyar. (CLR 'nin bunu çok büyük kesimler için yapamadığını unutmayın.) CLR daha sonra yeni segment isteklerini karşılamak için bu segmentleri kullanır. Uygulamanız yeni bir kesime bir dahaki sefer ihtiyaç duyduğunda, CLR, yeterince büyük bir bulması durumunda bu bekleme listesinden bir tane kullanır.

VM hoarding, bellek dışı özel durumların önüne geçmek için, sistemde çalışan baskın uygulamalar gibi bazı sunucu uygulamaları gibi zaten elde ettikleri kesimlerde tutmak isteyen uygulamalar için de yararlıdır.

Uygulamanızın oldukça kararlı bellek kullanımına sahip olduğundan emin olmak için bu özelliği kullandığınızda uygulamanızı dikkatle test etmenizi kesinlikle öneririz.
