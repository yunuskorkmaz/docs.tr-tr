---
title: Windows sistemlerde büyük nesne yığını
ms.date: 05/02/2018
helpviewer_keywords:
- large object heap (LOH)"
- LOH
- garbage collection, large object heap
- GC [.NET ], large object heap
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cdbbf3138cad0a2fae311bf03476eebba23b7320
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50202913"
---
# <a name="the-large-object-heap-on-windows-systems"></a>Windows sistemlerde büyük nesne yığını

.NET atık toplayıcı (GC) nesneleri küçük ve büyük nesneleri böler. Nesne büyük olduğunda bazı özniteliklerini nesne küçük olup olmadığını değerinden daha önemli hale gelir. Örneğin,--olan başka bir yerde yığında bellek kopyalama olan--sıkıştırma pahalı olabilir. Bu nedenle, .NET Atık toplayıcısının büyük nesneler büyük nesne yığınını (LOH) yerleştirir. Bu konu başlığında, büyük nesne yığını derinlemesine inceleyeceğiz. Bir nesne büyük bir nesne olarak ne niteliği taşır, bu büyük nesneler nasıl toplanır ve ne tür performans etkilerini büyük nesneler büyük oranda yansıtmaktadır açıklayacağız.

> [!IMPORTANT]
> Bu konu yalnızca Windows sistemleri üzerinde çalışan .NET Core ve .NET Framework içinde büyük nesne yığını açıklar. .NET uygulamaları diğer platformlarda çalışan LOH kapsamaz.

## <a name="how-an-object-ends-up-on-the-large-object-heap-and-how-gc-handles-them"></a>Bir nesne üzerinde büyük nesne yığını nasıl sona erer ve GC bunları nasıl işler?

Büyüktür veya eşittir 85.000 bayt için bir nesne ise, büyük bir nesneye dikkate almıştır. Bu sayı, performans ayarlama olarak belirlendi. Bir nesne ayırma isteği için 85.000 ya da daha fazla bayt olduğunda, çalışma zamanı büyük nesne yığınını ayırır.

Bunun ne anlama geldiğini anlamak için .NET GC hakkında bazı temel incelenmesi kullanışlıdır.

.NET Atık toplayıcısının generational Toplayıcı ' dir. Üç nesil vardır: nesil 0, 1. kuşak ve 2. nesil. 3 nesiller sahip olmak için, çoğu nesneler zar gen0, iyi ayarlanmış bir uygulamada nedenidir. Örneğin, istek tamamlandıktan sonra bir sunucu uygulamasında her istekle ilişkili ayırmaları öldürmüş. Yürütülen ayırma isteklerini gen1 olun ve öldürmüş vardır. Aslında, gen1 genç nesne alanları ve uzun süreli bir nesne alanları arasında bir tampon görevi görür.

Küçük nesneleri nesil 0 her zaman ayrılır ve kendi ömürlerine bağlı olarak, 1. kuşak ya da generation2 yükseltilebilir. Büyük nesneler, kuşak 2 olarak her zaman ayrılır.

Yalnızca 2. nesil toplama sırasında toplanan oldukları için büyük nesneler, kuşak 2 ait. Bir nesil toplandığında, tüm genç generation(s) de toplanır. Örneğin, 1. kuşak GC gerçekleştiğinde, her iki nesil 1 ve 0 toplanır. Ve 2. nesil GC gerçekleştiğinde, tam yığın toplanır. Bu nedenle, 2. nesil GC olarak da adlandırılan bir *tam GC*. Bu makalede tam GC yerine 2. nesil GC başvuruyor, ancak koşulları birbirinin yerine kullanılabilir.

Nesiller GC yığınında mantıksal bir görünümünü sağlar. Fiziksel olarak, yönetilen yığın segmentler Canlı nesneler. A *Yönetilen yığın segment* çağırarak OS GC ayırır bellek öbek [VirtualAlloc işlevi](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx) adına yönetilen kod. CLR yüklendiğinde, GC iki ilk öbek segmentini ayırır: küçük nesneleri (küçük nesne yığını veya SOH) için diğeri için büyük nesneler (büyük nesne yığını için).

İstek, koyarak ardından maddelerindeki ayırma yönetilen nesneler Bu yönetilen yığın kesimlerinde. Nesne 85.000 bayttan daha az ise segmenti için SOH yerleştirilir; Aksi takdirde, bir LOH kesiminde konur. Segment (küçük öbekler halinde) daha fazla uygulanır ve daha fazla nesne açtığına ayrılır.
SOH GC varlığını sürdürmesini nesneleri sonraki nesle yükseltilir. Bir nesil 0 toplamadan nesneler, kuşak 1 nesnelerinin artık kabul edilir ve benzeri. Ancak, eski nesil varlığını sürdürmesini nesneleri eski nesil olarak değerlendirilir. Diğer bir deyişle, gelen 2. nesil Dışarıda Kalanlar, 2. nesil nesneleri, ve (2. nesil ile toplanır) LOH nesneleri survivor LOH öğesinden gelir.

Kullanıcı kodu yalnızca nesil 0 (küçük nesne) veya LOH (büyük nesneler) ayırabilirsiniz. GC "nesneleri nesil 1 (nesil 0 ' survivor tanıtarak) ayırabilirsiniz yalnızca" ve nesil 2 (tarafından survivor nesil 1 ve 2 yükseltme).

Bir atık toplama işlemi tetiklendiğinde, GC Canlı nesneleri izler ve bunları sıkıştırır. Ancak sıkıştırma pahalı olduğundan GC *taramalar* LOH; daha sonra büyük nesne ayırma isteklerini karşılamak için yeniden kullanılabilir ölü nesneleri dışında boş bir liste sağlar. Bitişik ölü nesneleri ücretsiz tek bir nesne halinde yapılır.

.NET core ve .NET Framework'ü (.NET Framework 4.5.1 ile başlayarak) dahil <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode?displayProperty=nameWithType> LOH belirtme olanağı tanıyan bir özellik sırasında sonraki tam engelleme GC düzenlenmiş. Ve gelecekte .NET LOH otomatik olarak sıkıştırmak karar verebilirsiniz. Bu, büyük nesnelerin ayırmak ve bunlar taşıma emin olmak istiyorsanız, yine de bunları sabitleyin, anlamına gelir.

Şekil 1 GC forms sonra birinci nesil 0 atık Toplayıcı nesil 1 burada bir senaryo gösterilmektedir burada `Obj1` ve `Obj3` ölü olan ve forms 2. nesil birinci nesil 1 GC sonra nerede `Obj2` ve `Obj5` ölü olan. Bu ve aşağıdaki şekilde yalnızca gösterim amacıyla olduğunu unutmayın; daha iyi yığında ne göstermek için çok az sayıda nesneleri içerirler. Gerçekte çok daha fazla nesneyi GC genellikle faydalanırsınız.

![Şekil 1: Gen 0 GC ve gen 1 GC](media/loh/loh-figure-1.jpg)  
Şekil 1: Bir nesil 0 ve 1. kuşak GC.

Şekil 2 gösterir, 2. nesil GC sonra gördüğünüz `Obj1` ve `Obj2` ölü GC forms tarafından kullanılıyor kullanılan bellek yetersiz bitişik boş alan olan `Obj1` ve `Obj2`, daha sonra bir ayırma isteğini karşılamak için kullanıldı için `Obj4`. Son nesne sonra boşluk `Obj3`, ucuna da ayırma isteklerini karşılamak için kullanılabilir.

![Şekil 2: sonra 2. nesil GC](media/loh/loh-figure-2.jpg)  
Şekil 2: sonra 2. nesil GC

Büyük nesne ayırma isteklerini karşılamak için yeterli boş alan yoksa, GC ilk işletim sisteminden daha fazla kesim almaya çalışır. Bu başarısız olursa umuduyla bazı yer açmayı, içinde 2. nesil GC tetikler.

1. nesil veya 2. nesil GC sırasında atık toplayıcı olan Canlı nesne üzerinde işletim sistemine çağırarak parçaları sürümleri [VirtualFree işlevine](https://msdn.microsoft.com/library/windows/desktop/aa366892(v=vs.85).aspx). (Kısa ömürlü segment gen0/çöp toplayıcı bazı burada korumak gen1 canlı, çünkü burada kaydedilen üzerinde uygulamanızın içinde hemen ayırma dışında) sonra son Canlı nesne segmentin sonuna boşluk kaydı geri alınmış aynıdır. Ve bunlar, işletim Sisteminin bunları yeniden diske veri yazmak gerekmez anlamı sıfırlanır rağmen boş alanları kaydedilmiş kalır.

LOH segment, yalnızca LOH yalnızca 2. nesil GC'ler sırasında toplanan olduğundan, bu tür bir GC sırasında serbest bırakılabilir. Şekil 3, çöp toplayıcı'nın bir segmente (kesim 2) geri işletim sistemi sürümleri ve kalan segmentler hakkında daha fazla alan kaydeder burada bir senaryo gösterilmektedir. Kaydı geri alınmış boşluk kesim sonunda, büyük nesne ayırma isteklerini karşılamak için kullanması gereken, bellek yeniden kaydeder. (Bir işleme ve kaydetmek için hakkında açıklama belgelerine bakın [VirtualAlloc](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx).

![Şekil 3: LOH gen 2 GC sonra](media/loh/loh-figure-3.jpg)  
Şekil 3: 2. nesil GC sonra LOH

## <a name="when-is-a-large-object-collected"></a>Büyük nesne ne toplanır?

Genel olarak, aşağıdaki 3 koşullar gerçekleştiğinde GC oluşur:

- Ayırma, nesil 0 veya büyük nesne eşiği aşıyor.

  Eşik, bir oluşturma için kullanılan bir özelliktir. Çöp toplayıcı nesnelerin içine ayırdığında bir nesil için bir eşik ayarlanır. Eşik aşıldığında, o nesil GC tetiklenir. Küçük veya büyük nesneleri ayırdığınızda, nesil 0 ve LOH'ın eşikleri sırasıyla tükettiğiniz. Atık toplayıcı nesil 1 ve 2 ayırdığında kendi eşiklerini tüketir. Bu eşik, program çalışırken dinamik olarak ayarlanmıştır.

  Bu tipik bir durumdur; birçok GC'ye, yönetilen yığındaki ayırmalar nedeniyle gerçekleşir.

- <xref:System.GC.Collect%2A?displayProperty=nameWithType> Yöntemi çağrılır.

  Parametresiz <xref:System.GC.Collect?displayProperty=nameWithType> yöntemi çağrıldığında veya başka bir aşırı geçirilen <xref:System.GC.MaxGeneration?displayProperty=nameWithType> bağımsız değişken olarak, yönetilen yığının kalanını birlikte LOH toplanır.

- Düşük bellek durumda sistemidir.

  Çöp toplayıcı OS yüksek bellek bildirimi aldığında gerçekleşir. Atık toplayıcı nesil 2 GC yapılması üretken olmasını gördüğü ise bir tetikler.

## <a name="loh-performance-implications"></a>LOH performans etkileri

Büyük nesne yığını üzerindeki ayırmaları aşağıdaki yollarla performansı etkiler.

- Maliyet ayırma.

  CLR, verir her yeni nesne için bellek temizlenir garantisi sağlar. Bu, büyük nesne ayırma maliyetini tamamen (GC tetikler sürece) temizleme bellekle direncin hakim olduğu anlamına gelir. Bir bayt temizlemek için 2 döngüleri aldığı durumlarda en küçük büyük nesne temizlemek için 170,000 döngüleri alır. 2 GHz makinede 16 MB nesnesinin bellek temizleme yaklaşık 16ms alır. Daha kapsamlı bir maliyet olmasıdır.

- Maliyet koleksiyonu.

  2. nesil koleksiyonu ya da birinin eşik aşılırsa LOH ve 2. nesil birlikte toplanır çünkü tetiklenir. Bir nesil 2 toplama nedeniyle LOH tetiklenir, 2. nesil mutlaka sonra atık Toplayıcı çok daha küçük olmayacaktır. Nesil 2 kadar veri değilse, bu çok az etkisi yoktur. Ancak 2. nesil büyükse, 2. nesil birçok GC'ye tetiklenen performans sorunlarına neden olabilir. Birçok büyük nesneler üzerinde çok geçici olarak ayrılır ve büyük SOH varsa GC'ler yapılması çok fazla zaman harcama. Ayrıca, maliyet ayırma gerçekten ayırma ve gerçekten büyük nesnelerin özgür tutmak ekleyebilirsiniz.

- Başvuru türleri ile dizi öğeleri.

  LOH üzerindeki çok büyük nesneler genellikle (gerçekten büyük bir örnek nesne için çok nadir olduğu) dizilerdir. Bir dizinin öğeleri ise isteğe bağlı olarak başvuru açısından zengin, öğeleri değilse, var olmayan bir maliyeti doğurur zengin başvuru. Tüm başvuruları öğe içermiyorsa, çöp toplayıcı dizi boyunca hiç Git gerekmez. Örneğin, düğümlerin bir ikili ağaç biçiminde depolamak için bir dizi kullanın, düğümün gerçek düğümler tarafından sağ ve sol düğümüne başvurmak için uygulamak için bir yol şöyledir:

  ```csharp
  class Node
  {
     Data d;
     Node left;
     Node right;
  };

  Node[] binary_tr = new Node [num_nodes];
  ```

  Varsa `num_nodes` olan büyük, çöp toplayıcı öğe başına en az iki başvuru Git gerekir. Sağ ve sol düğümler dizinini depolamak için alternatif bir yoludur:

  ```csharp
  class Node
  {
     Data d;
     uint left_index;
     uint right_index;
  } ;
  ```

  Sol düğümün veri olarak başvuran yerine `left.d`, olarak başvurmanız `binary_tr[left_index].d`. Ve çöp toplayıcı sol ve sağ düğümü için tüm başvuruları bakmak gerekmez.

Üç dışında ilk iki genellikle üçüncü daha önemli faktörlerdir. Bu nedenle, geçici olanları ayırma yerine yeniden büyük nesnelerin bir havuz ayırmak önerilir.

## <a name="collecting-performance-data-for-the-loh"></a>LOH için performans verilerini toplama

Belirli bir alan için performans verilerini toplama önce aşağıdaki yapmış olduğunuz:

1. Bu adreste aramanız gereken kanıt bulundu.

2. Gördüğünüz performans sorunu açıklayan, hiçbir şey bulmadan bildiğiniz diğer alanları tükendi.

Web günlüğü postasına bakın [bir çözüm bulmak denemeden önce sorunu anlamak](https://blogs.msdn.microsoft.com/maoni/2006/09/01/understand-the-problem-before-you-try-to-find-a-solution/) bellek ve CPU temelleri hakkında daha fazla bilgi için.

LOH performans verilerini toplamak için aşağıdaki araçları kullanabilirsiniz:

- [.NET CLR bellek performans sayaçları](#net-clr-memory-performance-counters)

- [ETW olayları](#etw-events)

- [Bir hata ayıklayıcı](#a-debugger)

### <a name="net-clr-memory-performance-counters"></a>.NET CLR bellek performans sayaçları

Bu performans sayaçlarını genellikle performans sorunlarını araştırma, iyi bir ilk adım kaldı (kullanmanızı öneririz, ancak [ETW olayları](#etw)). Performans İzleyicisi, Şekil 4'te gösterildiği gibi istediğiniz sayaçları ekleyerek yapılandırın. LOH için uygun olan değerler şunlardır:

- **Gen 2 toplamaları sayısı**

   2. nesil GC'ler işlemi başladıktan sonra gerçekleşen sayısını görüntüler. (Tam çöp toplama olarak da bilinir) 2. nesil koleksiyonu sonunda sayaç artırılır. Bu sayaç gözlenen son değeri görüntüler.

- **Büyük nesne yığın boyutu**

   Boş disk alanı, LOH dahil olmak üzere bayt cinsinden geçerli boyutu, görüntüler. Bu sayaç her ayırma zaman bir atık toplama sonunda güncelleştirilir.

Performans İzleyicisi (perfmon.exe) performans sayaçlarını aramak için genel bir yoludur. Verdiğiniz işlemleri için ilgi çekici sayaç eklemek için "Sayaç Ekle" kullanın. Şekil 4'te gösterildiği gibi performans sayacı verileri bir günlük dosyasına kaydedebilirsiniz.

![Şekil 4: performans sayaçlarını ekleme.](media/loh/perfcounter.png)  
Şekil 4: 2. nesil GC sonra LOH

Performans sayaçları da programlı bir şekilde sorgulanabilir. Çoğu kişi, bunları kendi rutin test işleminin bir parçası olarak bu şekilde toplayın. Bunlar normal dışı değerleri sayaçlarla spot, bunlar başka bir yolla araştırmaya yardımcı olması için daha ayrıntılı veri almak için kullanın.

> [!NOTE]
> ETW çok daha zengin bilgi sağladığından ETW olaylarını kullanmanızı yerine performans sayaçları, öneririz.

### <a name="etw-events"></a>ETW olayları

Çöp toplayıcı ETW olayları yığın ne yaptığını anlamanıza yardımcı olması için zengin bir özellik kümesi sağlar ve neden. Aşağıdaki blog gönderileri, toplamak ve GC ETW olaylarıyla anlamak gösterilmektedir:

- [GC ETW olayları - 1](https://blogs.msdn.microsoft.com/maoni/2014/12/22/gc-etw-events-1/)

- [GC ETW olayları - 2](https://blogs.msdn.microsoft.com/maoni/2014/12/25/gc-etw-events-2/)

- [GC ETW olayları - 3](https://blogs.msdn.microsoft.com/maoni/2014/12/25/gc-etw-events-3/)

- [GC ETW olayları - 4](https://blogs.msdn.microsoft.com/maoni/2014/12/30/gc-etw-events-4/)

Aşırı kuşak 2 GC'ler geçici LOH ayırmaların neden tanımlamak için GC'ler için tetikleme nedeni sütununa bakın. Yalnızca büyük geçici nesnelerin ayıran basit bir test için ETW olaylarına aşağıdaki bilgi toplayabilir [PerfView](https://www.microsoft.com/download/details.aspx?id=28567) komut satırı:

```console
perfview /GCCollectOnly /AcceptEULA /nogui collect
```

Sonuç aşağıdakine benzer olacaktır:

![Şekil 5: ETW olayları PerfView kullanma İnceleme](media/loh/perfview.png)  
Şekil 5: PerfView kullanma gösterilen ETW olayları

Gördüğünüz gibi tüm GC'ler 2. GC'ye olan ve tüm büyük nesne ayırma bu GC tetiklenen yani AllocLarge tarafından tetiklenir. Bu ayırmalar geçici olduğunu biliyoruz çünkü **LOH hayatta kalma oranı %** sütun %1 söyler.

Bu büyük nesneler ayrılan size ek ETW olayları toplayabilir. Aşağıdaki komut satırı:

```console
perfview /GCOnly /AcceptEULA /nogui collect
```

yaklaşık her 100 bin cinsinden değer ayırmaların harekete geçirilen bir AllocationTick olay toplar. Diğer bir deyişle, her zaman büyük nesne ayrılmış bir olay harekete geçirilir. Ardından, büyük nesnelerin ayrılmış çağrı yığınını gösteren GC yığın ayırma görünümlerden birine göz atabilirsiniz:

![Şekil 6: Bir GC yığın ayırma görünümü](media/loh/perfview2.png)  
Şekil 6: Bir GC yığın ayırma görünümü

Gördüğünüz gibi yalnızca büyük nesneleri ayırdığı çok basit bir test budur kendi `Main` yöntemi.

### <a name="a-debugger"></a>Bir hata ayıklayıcı

Sahip olan bir bellek dökümü ve nesneleri gerçekten üzerinde LOH nedir Ara gerekir, kullanabileceğiniz [SoS hata ayıklama uzantısı](../../../docs/framework/tools/sos-dll-sos-debugging-extension.md) .NET tarafından sağlanan.

> [!NOTE]
> Bu bölümde belirtilen hata ayıklama komutları geçerli olan [Windows hata ayıklayıcıları](https://www.microsoft.com/whdc/devtools/debugging/default.mspx).

LOH çözümleme gelen örnek çıktı aşağıda gösterilmiştir:

```
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

LOH öbek boyutudur (16,754,224 + 16,699,288 + 16,284,504) = 49,738,016 bayt. Adresleri 023e1000 ve 033db630 arasında 8,008,736 bayt dizisi kapladığı <xref:System.Object?displayProperty=nameWithType> nesnelerini 6,663,696 bayt dizisi kapladığı <xref:System.Byte?displayProperty=nameWithType> nesneleri ve 2,081,792 bayt boş alan dolu.

Bazen, hata ayıklayıcı LOH toplam boyutu küçüktür 85.000 bayt olduğunu gösterir. Çalışma zamanının kendisi büyük bir nesneye daha küçük olan bazı nesneler ayrılacak LOH kullandığından bu gerçekleşir.

Bazen LOH sıkıştırılmamıştır çünkü LOH thoought parçalanma kaynağı olması olabilir. Parçalanma anlamına gelir:

- Yönetilen nesneler arasındaki boş alan miktarı tarafından belirtilen yönetilen yığının parçalanma. SoS içinde `!dumpheap –type Free` komut, yönetilen nesneler arasındaki boş alan miktarını görüntüler.

- Parçalanma bellek sanal bellek (VM) adres alanı olarak işaretlenmiş `MEM_FREE`. Windbg içinde çeşitli hata ayıklayıcı komutlarını kullanarak ulaşabilirsiniz.

   Aşağıdaki örnek, VM alanı parçalanma gösterir:

   ```
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

Çöp toplayıcısının sık yeni almak için yığın kesimlerini OS yönetilen ve boş olanları işletim sistemine yeniden sürüm gerektiren büyük geçici nesneler nedeniyle VM parçalanma görmek için daha yaygındır.

LOH VM parçalanmasına neden olup olmadığını doğrulamak için bir kesme noktası ayarlayabilirsiniz [VirtualAlloc](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx) ve [VirtualFree](https://msdn.microsoft.com/library/windows/desktop/aa366892(v=vs.85).aspx) kimin çağrı görmek için. Örneğin, kimlerin OS 8MBB daha büyük sanal bellek öbeklere ayırmak denedi görmek için şunun gibi bir kesme noktası ayarlayabilirsiniz:

```console
bp kernel32!virtualalloc "j (dwo(@esp+8)>800000) 'kb';'g'"
```

Bu komut ayıklayıcıya girer ve çağrı yığını yalnızca şu durumlarda gösterir [VirtualAlloc](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx) bir ayırma boyutu 8 MB (0x800000) değerinden büyük olarak adlandırılır.

CLR 2.0 denilen bir özelliği eklendi *VM Hoarding* , scenarious için yararlı olabilir burada kesim (yığın nesnesi büyük ve küçük üzerinde de dahil olmak üzere) sık alınan ve yayımlanmış. Adlı bir başlangıç bayrak belirttiğiniz VM Hoarding belirtmek için `STARTUP_HOARD_GC_VM` barındırma API'si aracılığıyla. İşletim sistemi boş segmentlere geri serbest bırakılması, yerine CLR bu segmentlerde belleği kaydeder ve onları bir bekleme listesine koyar. (CLR için çok büyük olduğundan kesimleri bunu değil olduğunu unutmayın.) CLR, yeni segment isteklerini karşılamak için daha sonra bu kesimler kullanır. Yeterince büyük bir bulabilirsiniz, uygulamanızın yeni bir segment duyduğunda bekleme listeden bir CLR kullanır.

VM hoarding de bunlar zaten, yetersiz bellek özel durumları engellemek için bu sistemde çalışan baskın uygulamalar, bazı sunucu uygulamaları gibi alınan parçaları üzerine tutmak istediğiniz uygulamalar için yararlıdır.

Uygulamanız olgunluğa bellek kullanımına sahip emin olmak için bu özelliği kullandığınızda, dikkatli bir şekilde uygulamanızı test etmenizi öneririz.
