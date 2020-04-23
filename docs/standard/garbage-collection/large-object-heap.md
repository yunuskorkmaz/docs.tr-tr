---
title: Windows'da büyük nesne yığını (LOH)
ms.date: 05/02/2018
helpviewer_keywords:
- large object heap (LOH)"
- LOH
- garbage collection, large object heap
- GC [.NET ], large object heap
ms.openlocfilehash: ab9beca58b3d6118bc0f5121b6f5dec71a9f9f36
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102274"
---
# <a name="the-large-object-heap-on-windows-systems"></a>Windows sistemlerinde büyük nesne yığını

.NET çöp toplayıcısı (GC) nesneleri küçük ve büyük nesnelere böler. Bir nesne büyükolduğunda, bazı öznitelikleri nesne küçükse daha önemli hale gelir. Örneğin, sıkıştırma,&mdash;yığın&mdash;başka bir yerde bellekte kopyalama pahalı olabilir. Bu nedenle, çöp toplayıcı büyük nesne yığını (LOH) üzerinde büyük nesneleri yerleştirir. Bu makalede, bir nesneyi büyük bir nesne olarak nitelenenler, büyük nesnelerin ne kadar toplandığı ve büyük nesnelerin ne tür performans etkileri dayattığı açıklanmaktadır.

> [!IMPORTANT]
> Bu makalede, .NET Framework ve .NET Core yalnızca Windows sistemlerinde çalışan büyük nesne yığını açıklanır. Diğer platformlarda .NET uygulamalarında çalışan LOH'yu kapsamaz.

## <a name="how-an-object-ends-up-on-the-loh"></a>Bir nesne LOH üzerinde nasıl biter?

Bir nesne 85.000 bayt boyutundan büyük veya eşitse, büyük bir nesne olarak kabul edilir. Bu sayı performans amıile belirlendi. Bir nesne ayırma isteği 85.000 veya daha fazla bayt için olduğunda, çalışma zamanı onu büyük nesne yığınına ayırır.

Bunun ne anlama geldiğini anlamak için, çöp toplayıcı sı hakkında bazı temel leri incelemek yararlıdır.

Çöp toplayıcı bir nesil koleksiyoncusudur. Üç kuşağı vardır: nesil 0, nesil 1 ve nesil 2. 3 nesil olmasının nedeni, iyi ayarlanmış bir uygulamada, çoğu nesnenin gen0'de ölmesidir. Örneğin, bir sunucu uygulamasında, her istekle ilişkili ayırmalar istek tamamlandıktan sonra ölür. Uçuş tahsis talepleri gen1'e dönüşecek ve orada ölecek. Esasen, gen1 genç nesne alanları ve uzun ömürlü nesne alanları arasında bir tampon görevi görür.

Küçük nesneler her zaman nesil 0'da ayrılır ve kullanım ömürlerine bağlı olarak nesil 1 veya nesil2'ye yükseltilebilir. Büyük nesneler her zaman nesil 2'de ayrılır.

Büyük nesneler nesil 2'ye aittir, çünkü yalnızca nesil 2 koleksiyonu sırasında toplanır. Bir nesil toplandığında, tüm genç nesil (ler) de toplanır. Örneğin, bir nesil 1 GC gerçekleştiğinde, hem nesil 1 hem de 0 toplanır. Ve bir nesil 2 GC olduğunda, tüm yığın toplanır. Bu nedenle, bir nesil 2 GC de *tam GC*denir. Bu makalede, tam GC yerine nesil 2 GC anlamına gelir, ancak terimler değiştirilebilir.

Nesiller GC yığınının mantıksal bir görünümünü sağlar. Fiziksel olarak, nesneler yönetilen yığın segmentlerde yaşar. *Yönetilen yığın kesimi,* Yönetilen kod adına [VirtualAlloc işlevini](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) arayarak GC'nin işletim sistemi tarafından rezerve ettiği bir bellek yığınıdır. CLR yüklendiğinde, GC iki başlangıç yığını ayırır: biri küçük nesneler (küçük nesne yığını veya SOH) ve biri büyük nesneler (büyük nesne yığını) için.

Ayırma istekleri daha sonra yönetilen nesneleri bu yönetilen yığın kesimlerine koyarak karşılanır. Nesne 85.000 bayttan azsa, SOH için segmente konur; aksi takdirde, bir LOH segmenti üzerine konur. Daha fazla nesne onlara ayrıldıkça, segmentler (daha küçük parçalar halinde) işlenir.
SOH için, bir GC hayatta nesneler sonraki nesile yükseltilir. Bir nesil 0 koleksiyonu hayatta nesneler artık nesil 1 nesneleri olarak kabul edilir, ve benzeri. Ancak, en eski nesil hayatta nesneler hala en eski nesil olarak kabul edilir. Başka bir deyişle, nesil 2'den hayatta kalanlar nesil 2 nesneleridir; ve LOH kurtulanların LOH nesneleri (gen2 ile toplanır).

Kullanıcı kodu yalnızca nesil 0 (küçük nesneler) veya LOH (büyük nesneler) olarak tahsis edilebilir. Sadece GC, nesil 1'deki nesneleri (nesil 0'dan kurtulanları teşvik ederek) ve nesil 2'de (1 ve 2. nesilden kurtulanları teşvik ederek) "tahsis edebilir".

Bir çöp toplama tetiklendiğinde, GC canlı nesneleri izler ve sıkıştırılır. Ama sıkıştırma pahalı olduğu için, GC LOH *süpürür;* daha sonra büyük nesne ayırma isteklerini karşılamak için yeniden kullanılabilecek ölü nesnelerden ücretsiz bir liste yapar. Bitişik ölü nesneler tek bir boş nesne haline getirilir.

.NET Core ve .NET Framework (.NET Framework 4.5.1 ile başlayarak) kullanıcıların bir sonraki tam engelleme GC sırasında LOH sıkıştırılmış olması gerektiğini belirtmelerini sağlayan <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode?displayProperty=nameWithType> özelliği içerir. Ve gelecekte, .NET Otomatik olarak LOH sıkıştırmaya karar verebilir. Bu, büyük nesneleri ayırDığınız ve hareket etmediklerinden emin olmak istiyorsanız, yine de sabitlemeniz gerektiği anlamına gelir.

Şekil 1, GC'nin ilk nesil 0 GC'den `Obj1` sonra `Obj3` nesil 1'i oluşturduğu ve nerede ve ölü `Obj2` `Obj5` olduğu ilk nesil 1 GC'den sonra nesil 2'yi oluşturduğu bir senaryoyu göstermektedir. Bu ve aşağıdaki şekillerin yalnızca illüstrasyon amaçlı olduğunu unutmayın; yığında ne olduğunu daha iyi göstermek için çok az nesne içerirler. Gerçekte, çok daha fazla nesne genellikle bir GC yer almaktadır.

![Şekil 1: Bir gen 0 GC ve bir gen 1 GC](media/loh/loh-figure-1.jpg)\
Şekil 1: Bir nesil 0 ve bir nesil 1 GC.

Şekil 2 bir nesil sonra gösterir 2 `Obj1` `Obj2` GC bu gördüm ve ölü, GC tarafından işgal edildi `Obj1` ve `Obj2`daha sonra bir tahsis isteği karşılamak `Obj4`için kullanılan bellek bitişik boş alan oluşturur . Son nesneden sonraki `Obj3`boşluk, segmentin sonuna kadar ayırma isteklerini karşılamak için de kullanılabilir.

![Şekil 2: Bir gen 2 GC sonra](media/loh/loh-figure-2.jpg)\
Şekil 2: Bir nesil sonra 2 GC

Büyük nesne ayırma isteklerini karşılamak için yeterli boş alan yoksa, GC önce işletim sistemi'nden daha fazla segment elde etmeye çalışır. Bu başarısız olursa, bir nesil tetikler 2 GC biraz yer boşaltma umuduyla.

Bir nesil 1 veya nesil 2 GC sırasında, çöp toplayıcı [VirtualFree işlevini](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree)çağırarak işletim sistemi geri üzerinde hiçbir canlı nesne var segmentleri bültenleri. Segmentin sonuna kadar ki son canlı nesneden sonraki boşluk ayrılır (gen0/gen1'in yaşadığı geçici segment dışında, çöp toplayıcının bazı larını bağlı tuttuğu, çünkü uygulamanız hemen içinde tahsis edilecektir). Ve boş alanlar sıfırlanır, yani işletim sistemi diske geri veri yazmak gerekmez kararlı kalır.

LOH sadece nesil 2 GCs sırasında toplanır yana, LOH segmenti sadece böyle bir GC sırasında serbest bırakılabilir. Şekil 3, çöp toplayıcının bir kesimi (segment 2) işletim sistemi için geri saldığı ve kalan segmentlerde daha fazla alan ayırdığı bir senaryoyu göstermektedir. Büyük nesne ayırma isteklerini karşılamak için kesimin sonundaki adanmış alanı kullanması gerekiyorsa, belleği yeniden işler. (Commit/decommit bir açıklama için, [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc)için belgelere bakın.

![Şekil 3: LOH sonra bir gen 2 GC](media/loh/loh-figure-3.jpg)\
Şekil 3: Bir nesil 2 GC sonra LOH

## <a name="when-is-a-large-object-collected"></a>Büyük bir nesne ne zaman toplanır?

Genel olarak, bir GC aşağıdaki üç koşuldan biri altında oluşur:

- Ayırma, nesil 0 veya büyük nesne eşiğini aşıyor.

  Eşik bir neslin özelliğidir. Çöp toplayıcı nesneleri içine ayırdığında bir nesil için bir eşik ayarlanır. Eşik aşıldığında, o nesilde bir GC tetiklenir. Küçük veya büyük nesneleri ayırdığınızda, sırasıyla nesil 0 ve LOH eşiklerini tüketirsiniz. Çöp toplayıcısı nesil 1 ve 2'ye ayrıldıklarında, eşiklerini tüketir. Program çalışırken bu eşikler dinamik olarak ayarlanır.

  Bu tipik bir durumdur; çoğu GC, yönetilen yığındaki ayırmalar nedeniyle gerçekleşir.

- Yöntem <xref:System.GC.Collect%2A?displayProperty=nameWithType> denir.

  Parametresiz <xref:System.GC.Collect?displayProperty=nameWithType> yöntem çağrılır veya başka <xref:System.GC.MaxGeneration?displayProperty=nameWithType> bir aşırı yük bir bağımsız değişken olarak geçirilirse, LOH yönetilen yığının geri kalanı ile birlikte toplanır.

- Sistem düşük bellek durumunda.

  Bu, çöp toplayıcı işletim sistemi yüksek bellek bildirimi aldığında oluşur. Çöp toplayıcı bir nesil 2 GC yapmanın verimli olacağını düşünüyorsa, bir tetikler.

## <a name="loh-performance-implications"></a>LOH performans etkileri

Büyük nesne yığınıüzerindeki ayırmalar performansı aşağıdaki şekillerde etkiler.

- Tahsis maliyeti.

  CLR, verdiği her yeni nesnenin belleği temizlenir garantisi verir. Bu, büyük bir nesnenin ayırma maliyetinin bellek temizleme tarafından tamamen baskın olduğu anlamına gelir (gc tetiklemediği sürece). Bir bayttemizlemek için 2 döngü gerekiyorsa, en küçük büyük nesneyi temizlemek için 170.000 döngü alır. 2GHz makinedeki 16MB'lık bir nesnenin belleği temizlemek yaklaşık 16 m sürer. Bu oldukça büyük bir bedel.

- Tahsilat maliyeti.

  LOH ve nesil 2 birlikte toplandığı için, birinin eşiği aşılırsa, bir nesil 2 koleksiyonu tetiklenir. LOH nedeniyle bir nesil 2 koleksiyonu tetiklenirse, nesil 2 mutlaka GC sonra çok daha küçük olmayacaktır. Nesil 2 hakkında çok fazla veri yoksa, bu en az etkiye sahiptir. Ancak nesil 2 büyükse, birçok nesil 2 GC tetiklenirse performans sorunlarına neden olabilir. Birçok büyük nesneler çok geçici olarak tahsis edilir ve büyük bir SOH varsa, GCs yaparken çok fazla zaman harcama olabilir. Buna ek olarak, gerçekten büyük nesneleri ayırmaya ve bırakmaya devam ederseniz, tahsis maliyeti gerçekten ekleyebilirsiniz.

- Başvuru türlerine sahip dizi öğeleri.

  LOH üzerinde çok büyük nesneler genellikle diziler (gerçekten büyük bir örnek nesne olması çok nadirdir). Bir dizinin öğeleri referans açısından zenginse, öğeler referans açısından zengin değilse, bulunmayan bir maliyete neden olur. Öğe herhangi bir başvuru içermiyorsa, çöp toplayıcının diziden geçmesi gerekmez. Örneğin, düğümleri ikili bir ağaçta depolamak için bir dizi kullanıyorsanız, bunu uygulamanın bir yolu, bir düğümün sağ ve sol düğümüne gerçek düğümler tarafından başvurmaktır:

  ```csharp
  class Node
  {
     Data d;
     Node left;
     Node right;
  };

  Node[] binary_tr = new Node [num_nodes];
  ```

  `num_nodes` Büyükse, çöp toplayıcının öğe başına en az iki başvurudan geçmesi gerekir. Alternatif bir yaklaşım, sağ ve sol düğümdizisini depolamaktır:

  ```csharp
  class Node
  {
     Data d;
     uint left_index;
     uint right_index;
  } ;
  ```

  Sol düğümün verilerini " olarak `left.d` `binary_tr[left_index].d`adlandırmak yerine. Ve çöp toplayıcı sol ve sağ düğüm için herhangi bir referans bakmak gerekmez.

Üç faktörden, ilk ikisi genellikle üçüncüfaktörden daha önemlidir. Bu nedenle, geçici nesneler ayırmak yerine yeniden kullandığınız büyük nesnelerden oluşan bir havuz ayırmanızı öneririz.

## <a name="collect-performance-data-for-the-loh"></a>LOH için performans verileri toplama

Belirli bir alan için performans verileri toplamadan önce aşağıdakileri zaten yapmış olmalısınız:

1. Bu bölgeye bakmanız gerektiğine dair kanıt buldum.

2. Gördüğünüz performans sorununu açıklayabilecek hiçbir şey bulamadan bildiğiniz diğer alanları tükettiniz.

Bloga bakın Bellek ve CPU temelleri hakkında daha fazla bilgi için [bir çözüm bulmaya çalışmadan önce sorunu anlayın.](https://devblogs.microsoft.com/dotnet/understand-the-problem-before-you-try-to-find-a-solution/)

LOH performansı hakkında veri toplamak için aşağıdaki araçları kullanabilirsiniz:

- [.NET CLR bellek performans sayaçları](#net-clr-memory-performance-counters)

- [ETW olayları](#etw-events)

- [Hata ayıklama](#a-debugger)

### <a name="net-clr-memory-performance-counters"></a>.NET CLR Bellek Performans sayaçları

Bu performans sayaçları genellikle performans sorunlarını araştırmak için iyi bir ilk adımdır [(etw olaylarını](#etw-events)kullanmanızı öneririmıza rağmen). Şekil 4'ün gösterdiği gibi, istediğiniz sayaçları ekleyerek Performans Monitörü'ne yapılandırırsınız. LOH ile ilgili olanlar şunlardır:

- **Gen 2 Koleksiyonları**

   İşlemin başlamasından bu yana nesil 2 GC'lerin oluşma sayısını görüntüler. Sayaç, bir nesil 2 koleksiyonunun sonunda (tam çöp toplama olarak da adlandırılır) artıyla şıvlanır. Bu sayaç, gözlenen son değeri görüntüler.

- **Büyük Nesne Yığını boyutu**

   LOH'un boş alan da dahil olmak üzere geçerli boyutunu baytlar halinde görüntüler. Bu sayaç, her ayırmada değil, çöp toplamanın sonunda güncelleştirilir.

Performans sayaçlarına bakmanın yaygın bir yolu Performance Monitor (perfmon.exe) iledir. Önemsediğiniz işlemler için ilginç sayacı eklemek için "Sayaç Ekle"yi kullanın. Şekil 4'ün gösterdiği gibi performans sayacı verilerini bir günlük dosyasına kaydedebilirsiniz:

![Performans sayaçları eklemeyi gösteren ekran görüntüsü.](media/large-object-heap/add-performance-counter.png)
Şekil 4: Bir nesil 2 GC sonra LOH

Performans sayaçları da programlı olarak sorgulanabilir. Birçok kişi rutin test sürecinin bir parçası olarak bu şekilde toplamak. Sıra dışı değerlere sahip sayaçları tespit ettiklerinde, soruşturmaya yardımcı olmak için daha ayrıntılı veriler elde etmek için başka araçlar kullanırlar.

> [!NOTE]
> ETW çok daha zengin bilgiler sağladığından, performans sayaçları yerine ETW etkinliklerini kullanmanızı öneririz.

### <a name="etw-events"></a>ETW olayları

Çöp toplayıcı, yığının ne yaptığını ve neden yaptığını anlamanıza yardımcı olmak için zengin bir ETW olayı kümesi sağlar. Aşağıdaki blog gönderileri, ETW ile GC etkinliklerinin nasıl toplandığını ve anlayacağımı gösterir:

- [GC ETW Etkinlikleri - 1](https://devblogs.microsoft.com/dotnet/gc-etw-events-1/)

- [GC ETW Etkinlikleri - 2](https://devblogs.microsoft.com/dotnet/gc-etw-events-2/)

- [GC ETW Etkinlikleri - 3](https://devblogs.microsoft.com/dotnet/gc-etw-events-3/)

- [GC ETW Etkinlikleri - 4](https://devblogs.microsoft.com/dotnet/gc-etw-events-4/)

Geçici LOH ayırmalarının neden olduğu aşırı nesil 2 GC'leri tanımlamak için, GC'ler için Tetikleme Nedeni sütununa bakın. Yalnızca geçici büyük nesneler ayıran basit bir sınama için, aşağıdaki [PerfView](https://www.microsoft.com/download/details.aspx?id=28567) komut satırıyla ETW olayları hakkında bilgi toplayabilirsiniz:

```console
perfview /GCCollectOnly /AcceptEULA /nogui collect
```

Sonuç şu şekildedir:

![PerfView'deki ETW olaylarını gösteren ekran görüntüsü.](media/large-object-heap/event-tracing-windows-perfview.png)
Şekil 5: PerfView kullanılarak gösterilen ETW olayları

Gördüğünüz gibi, tüm GC'ler nesil 2 GC'lerdir ve hepsi AllocLarge tarafından tetiklenir, bu da büyük bir nesnenin ayrılmasının bu GC'yi tetiklediği anlamına gelir. **LOH Survival Rate %** sütununda %1 yazdığı için bu ayırmaların geçici olduğunu biliyoruz.

Bu büyük nesneleri kimin ayırdığını söyleyen ek ETW olayları toplayabilirsiniz. Aşağıdaki komut satırı:

```console
perfview /GCOnly /AcceptEULA /nogui collect
```

yaklaşık her 100k değerindeki tahsisatları ateşleyen bir TahsisatTick olayı toplar. Başka bir deyişle, büyük bir nesne her tahsis edide bir olay ateşlenir. Daha sonra, büyük nesneleri ayıran çağrı yığınlarını gösteren GC Heap Alloc görünümlerinden birine bakabilirsiniz:

![Çöp toplayıcı yığını görünümünü gösteren ekran görüntüsü.](media/large-object-heap/garbage-collector-heap.png)
Şekil 6: Bir GC Yığın Alloc görünümü

Gördüğünüz gibi, bu sadece `Main` kendi yönteminden büyük nesneleri ayıran çok basit bir testtir.

### <a name="a-debugger"></a>Hata ayıklama

Sahip olduğunuz tek şey bir bellek dökümüyse ve LOH'da gerçekte hangi nesnelere sahip seniz, .NET tarafından sağlanan [SoS hata ayıklama uzantısını](../../../docs/framework/tools/sos-dll-sos-debugging-extension.md) kullanabilirsiniz.

> [!NOTE]
> Bu bölümde belirtilen hata ayıklama komutları Windows [Hata Ayıklayıcıları](https://www.microsoft.com/whdc/devtools/debugging/default.mspx)için geçerlidir.

Aşağıdaki LOH analiz örnek çıktı gösterir:

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

LOH yığın boyutu (16.754.224 + 16.699.288 + 16.284.504) = 49.738.016 bayt. 023e1000 ve 033db630 adresleri arasında, 8.008.736 bayt <xref:System.Object?displayProperty=nameWithType> bir dizi nesne tarafından işgal edilir, 6.663.696 bayt <xref:System.Byte?displayProperty=nameWithType> nesnelerin bir dizi tarafından işgal edilir ve 2.081.792 bayt boş alan tarafından işgal edilir.

Bazen hata ayıklama, LOH'un toplam boyutunun 85.000 bayttan az olduğunu gösterir. Çalışma zamanının kendisi büyük bir nesneden daha küçük bazı nesneleri ayırmak için LOH'yu kullandığından bu durumda olur.

LOH sıkıştırılmış olmadığından, bazen LOH parçalanma kaynağı olduğu düşünülmektedir. Parçalanma nın anlamı:

- Yönetilen nesneler arasındaki boş alan miktarıyla gösterilen yönetilen yığının parçalanması. SoS'ta `!dumpheap –type Free` komut, yönetilen nesneler arasındaki boş alan miktarını görüntüler.

- Sanal bellek parçalanma (VM) adres alanı, bellek olarak `MEM_FREE`işaretlenmiş olan . Windbg çeşitli hata ayıklama komutları kullanarak alabilirsiniz.

   Aşağıdaki örnekvm alanında parçalanma gösterir:

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

Çöp toplayıcısının işletim sistemi'nden sık sık yeni yönetilen yığın segmentleri edinmesini ve boş olanları işletim sistemi'ne geri salmasını gerektiren geçici büyük nesnelerden kaynaklanan VM parçalanmasını görmek daha yaygındır.

LOH VM parçalanma neden olup olmadığını doğrulamak için, onları aramak kim görmek için [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) ve [VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree) bir kesme noktası ayarlayabilirsiniz. Örneğin, işletim sistemi 8MBB'den daha büyük sanal bellek parçalarını kimin ayırmaya çalıştığını görmek için aşağıdaki gibi bir kesme noktası ayarlayabilirsiniz:

```console
bp kernel32!virtualalloc "j (dwo(@esp+8)>800000) 'kb';'g'"
```

Bu komut hata ayıklayıcıya girer ve yalnızca [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) 8MB'dan (0x80000) büyük bir ayırma boyutuyla çağrıldığında çağrı yığınını gösterir.

CLR 2.0, segmentlerin (büyük ve küçük nesne yığınları dahil) sık sık alınıp serbest bırakıldığı senaryolar için yararlı olabilecek *VM Hoarding* adlı bir özellik ekledi. VM Istifleme belirtmek için, barındırma `STARTUP_HOARD_GC_VM` API'si üzerinden çağrılan bir başlangıç bayrağı belirtirsiniz. CLR, boş segmentleri işletim sistemi için geri serbest bırakmak yerine, bu segmentlerde bellek decommits ve bekleme listesine koyar. (CLR'nin bunu çok büyük segmentler için yapmadığını unutmayın.) CLR daha sonra bu segmentleri yeni segment isteklerini karşılamak için kullanır. Uygulamanızın yeni bir segmente ihtiyacı olduğunda, CLR yeterince büyük bir segment bulabilirse bu bekleme listesinden bir tane kullanır.

VM istifleme, bellek dışında özel durumları önlemek için sistemde çalışan baskın uygulamalar olan bazı sunucu uygulamaları gibi zaten edindikleri segmentleri tutmak isteyen uygulamalar için de yararlıdır.

Uygulamanızın oldukça kararlı bellek kullanımına sahip olduğundan emin olmak için bu özelliği kullandığınızda uygulamanızı dikkatle test etmenizi öneririz.
