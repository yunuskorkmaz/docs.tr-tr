---
title: Windows sistemlerinde büyük nesne yığın
ms.date: 05/02/2018
helpviewer_keywords:
- large object heap (LOH)"
- LOH
- garbage collection, large object heap
- GC [.NET ], large object heap
author: rpetrusha
ms.author: ronpet
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: abb1f72a10a4aff448dea22b5c9415111c25eaab
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/23/2018
---
# <a name="the-large-object-heap-on-windows-systems"></a>Windows sistemlerinde büyük nesne yığın

.NET Atık toplayıcısının (GC) nesneleri küçük ve büyük nesneleri böler. Bir nesne büyük olduğunda bazı özniteliklerini nesne küçük olup olmadığını daha önemli ölçüde haline gelir. Örneğin, buna--öbek herhangi bir yerinde bellekte kopyalama olan--sıkıştırılmasını pahalı olabilir. Bu nedenle, .NET Atık toplayıcısının büyük nesneler büyük nesne yığın (LOH) yerleştirir. Bu konuda, büyük nesne Yığın derinliği inceleyeceğiz. Hangi nesne büyük nesne olarak niteleyen, bu büyük nesneler nasıl toplanır ve ne tür performans etkileri büyük nesneler zorunlu tuttukları ele alacağız.

> [!IMPORTANT]
> Bu konu yalnızca Windows sistemlerinde çalışan .NET Core ve .NET Framework içinde büyük nesne yığın açıklar. .NET uygulamaları diğer platformlarda çalışan LOH kapsamaz.

## <a name="how-an-object-ends-up-on-the-large-object-heap-and-how-gc-handles-them"></a>Bir nesne üzerinde büyük nesne yığın nasıl sona erer ve GC bunları nasıl işler?

Bir nesne 85. 000 bayta eşit veya daha büyük ise, büyük nesne dikkate almıştır. Bu sayı, performans ayarlama belirlendi. Bir nesne ayırma isteği için 85. 000 ya da daha fazla bayt olduğunda, çalışma zamanı üzerinde büyük nesne yığın ayırır.

Bunun ne anlama geldiği anlamak için .NET GC hakkında bazı temelleri incelemek kullanışlıdır.

.NET Atık toplayıcısının bir kişinin Toplayıcı ' dir. Üç nesil vardır: kuşak 0, 1. nesil ve 2. nesil. 3 nesli sahip olmak için, çoğu nesneleri dökme gen0 içinde iyi ayarlanmış bir uygulamasında nedenidir. Örneğin, istek tamamlandıktan sonra bir sunucu uygulamasında her istekle ilişkili ayırmaları öldürmüş. Yürütülen ayırma isteklerini gen1 kolaylaştırır ve öldürmüş vardır. Esas olarak, gen1 Küçük yaştaki nesne alanları ve uzun süreli nesne alanları arasında bir tampon görevi görür.

Küçük nesneleri oluşturma 0 her zaman ayrılır ve kendi ömürleri bağlı olarak, 1. nesil veya generation2 yükseltilebilir. Büyük nesneler, nesil 2 her zaman ayrılır.

Yalnızca 2. nesil derleme sırasında toplanan çünkü bunlar büyük nesneler 2. nesil ait. Bir oluşturma toplandığında, tüm küçük generation(s) de toplanır. Örneğin, 1. nesil GC gerçekleştiğinde, her iki nesil 1 ve 0 toplanır. Ve 2. nesil GC gerçekleştiğinde, tüm yığın toplanır. Bu nedenle, 2. nesil GC olarak da adlandırılan bir *tam GC*. 2. nesil GC tam GC yerine bu makalede başvuruyor, ancak koşulları birbirinin yerine kullanılabilir.

Nesli GC yığını mantıksal bir görünümünü sağlar. Fiziksel olarak, nesneleri Yönetilen yığın segmentlerinde dinamik. A *Yönetilen yığın segment* bir öbektir çağırarak OS GC ayırır bellek [VirtualAlloc işlevi](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx) yönetilen kod adına. CLR yüklendiğinde GC iki ilk öbek kesimi ayırır: küçük nesneleri (küçük nesne yığın veya SOH) için diğeri için büyük nesneler (büyük nesne yığın).

İstekleri sonra memnun koyarak ayırma yönetilen nesneler üzerinde bu Yönetilen yığın kesimler. 85. 000 bayt'tan küçük nesneyse için SOH kesiminde yerleştirilir; Aksi halde, bir LOH kesiminde yerleştirilir. Segment (daha küçük parçalar) daha fazla yapıldığından ve daha fazla nesneleri açtığına ayrılmaz.
SOH için GC varlığını sürdürmesini nesneleri nesil için öne çıkar. Kuşak 0 koleksiyonu varlığını sürdürmesini nesneler artık kuşak 1 nesnelerinin olarak kabul edilir ve benzeri. Ancak, eski kuşak varlığını sürdürmesini nesneler hala eski nesil olduğu kabul edilir. Diğer bir deyişle, 2. nesil gelen survivors 2. nesil nesneleridir; ve LOH gelen survivors (hangi gen2 ile toplanan) LOH nesneleridir. 

Kullanıcı kodu yalnızca 0 (küçük nesneler) veya (büyük nesneler) LOH oluşturma tahsis edebilirsiniz. GC "nesneleri nesil 1 (0 kuşaktan survivors yükselterek) tahsis edebilirsiniz yalnızca" ve (tarafından survivors 1 ve 2 nesli yükseltme) 2. nesil.

Çöp toplama tetiklendiğinde GC dinamik nesneler arasında izler ve bunları sıkıştırır. Ancak sıkıştırma pahalıdır GC *taramalar* LOH; daha sonra büyük nesne ayırma isteklerini karşılamak için yeniden kullanılabilir ölü nesneleri dışında boş bir liste sağlar. Bitişik ölü nesneleri bir ücretsiz nesnesine yapılır.

.NET core ve .NET Framework'ü (.NET Framework 4.5.1 ile başlayarak) dahil <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode?displayProperty="fullname"> belirtmek için LOH kullanıcılara özelliği sırasında sonraki tam engelleme GC düzenlenmiş. Ve .NET LOH otomatik olarak compact gelecekte karar verebilirsiniz. Bu büyük nesneler ayırmak ve bunlar taşıma emin olmak istiyorsanız, yine bunları sabitleyebilirsiniz, anlamına gelir.

Şekil 1 burada GC forms 1. nesil birinci nesil 0 GC sonra bir senaryo gösterilmektedir nerede `Obj1` ve `Obj3` ölü olan ve forms 2. nesil birinci nesil 1 GC sonra burada `Obj2` ve `Obj5` ölü şunlardır. Bu ve aşağıdaki rakamları yalnızca gösterim amacıyla olduğunu unutmayın; daha iyi öbek üzerinde olanlar göstermek için çok az sayıda nesneleri içerirler. Gerçekte, pek çok nesne, genellikle bir GC ilgilidir.

![Şekil 1: Gen 0 GC ve gen 1 GC](media/loh/loh-figure-1.jpg)   
Şekil 1: Kuşak 0 ve 1. nesil GC.

Şekil 2 gösterir, 2. nesil GC sonra gördüğünüz `Obj1` ve `Obj2` olan GC forms bitişik boş alanı tarafından akacağını kullanılan bellek tükendi ölü `Obj1` ve `Obj2`, o ayırma isteği karşılamak için kullanıldı için `Obj4`. Son nesne sonra boşluk `Obj3`, segmentinin sonunu ayrıca ayırma isteklerini karşılamak için kullanılabilir.
 
![Şekil 2: sonra gen 2 GC](media/loh/loh-figure-2.jpg)  
Şekil 2: sonra 2. nesil GC

Büyük nesne ayırma isteklerini karşılamak için yeterli boş alan yoksa GC önce işletim sistemi daha fazla bölümlerinin almaya çalışır. Başarısız olursa, 2. nesil GC biraz alan boşaltın boşaltma, soluk içinde tetikler.

1. nesil veya 2. nesil GC sırasında dinamik Nesne üzerlerinde işletim sistemine geri çağırarak sahip atık toplayıcı serbest [VirtualFree işlevi](https://msdn.microsoft.com/library/windows/desktop/aa366892(v=vs.85).aspx). (Burada gen0/atık toplayıcı bazı burada korumak gen1 canlı, çünkü kaydedilen kısa ömürlü kesiminde uygulamanız içinde hemen ayırma dışında) segmentinin sonunu son Canlı nesnesine sonra kaydı geri alınmış alanıdır. Ve bunlar, işletim sistemi veri bunları yeniden diske yazma gerekmez anlamı sıfırlanır olsa boş alanları kaydedilmiş kalır.

LOH kesimi, yalnızca LOH yalnızca 2. nesil GC'ler sırasında toplanan olduğundan, bu tür bir GC sırasında serbest. Şekil 3 burada atık toplayıcı bir segmente (kesim 2) geri işletim sistemi sürümleri ve kalan segmentler hakkında daha fazla alan decommits bir senaryo gösterilmektedir. Büyük nesne ayırma isteklerini karşılamak için kesim sonunda kaydı geri alınmış alan kullanması gerekirse, bellek yeniden kaydeder. (Bir açıklaması tamamlama ve kaydettikleri için belgelerine bakın [VirtualAlloc](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx).
 
![Şekil 3: LOH gen 2 GC sonra](media/loh/loh-figure-3.jpg)  
Şekil 3: 2. nesil GC sonra LOH

## <a name="when-is-a-large-object-collected"></a>Ne zaman büyük nesne toplanır?

Genel olarak, aşağıdaki 3 aşağıdaki koşullardan biri gerçekleştiğinde bir GC oluşur:

- Ayırma kuşak 0 veya büyük nesne eşiği aşıyor.

   Eşik bir nesil bir özelliktir. Çöp toplayıcı nesneleri içine ayırdığında bir oluşturma için bir eşik ayarlanır. Eşik aşıldığında, GC üzerinde nesil tetiklenir. Küçük veya büyük nesneleri tahsis ettiğinizde, kuşak 0 ve LOH'ın eşikleri, sırasıyla tüketir. Çöp toplayıcı 1 ve 2. nesil ayırdığında kendi eşiklerini tüketir. Program çalışırken bu eşikler dinamik olarak ayarlanmıştır.

   Bu normal bir durumdur; yönetilen yığında ayırmalar nedeniyle çoğu GC'ler gerçekleşir.

- <xref:System.GC.Collect%2A?displayProperty=nameWithType> Yöntemi çağrılır.

   Varsa parametresiz <xref:System.GC.Collect?displayProperty=nameWithType> yöntemi çağrıldığında veya başka bir aşırı geçirilen <xref:System.GC.MaxGeneration?displayProperty=nameWithType> bir bağımsız değişken olarak yönetilen yığın geri kalanı ile birlikte LOH toplanır.

- Düşük bellek durumda sistemidir.

   Çöp toplayıcı OS yüksek bellek bildirimi aldığında bu oluşur. 2. nesil GC yapılması üretken olmasını atık toplayıcı düşündüğü, bir tetikler.

## <a name="loh-performance-implications"></a>LOH performans etkileri

Ayırmalar büyük nesne yığın üzerinde aşağıdaki yollarla performansını etkiler.

- Maliyet ayırma.

   CLR verir bellek her yeni nesne için temizlenir garantisi yapar. Bu, büyük nesne ayırma maliyetini tamamen (GC tetikler sürece) temizleyerek bellek tarafından hâkim anlamına gelir. Bir bayt temizlemek için 2 döngüleri geçen en küçük büyük nesne temizlemek için 170,000 döngüleri kazanır. 2 GHz makine 16 MB nesnesinde memmory temizleme yaklaşık 16ms alır. Bunun yerine büyük bir maliyet olmasıdır.

- Maliyet koleksiyonu.

   Herhangi birinin eşik aşılırsa LOH ve 2. nesil birlikte toplanır olduğundan, 2. nesil koleksiyonu tetiklenir. 2 koleksiyonu nedeniyle LOH tetiklenir oluşturma, 2. nesil mutlaka GC sonra çok daha küçük olmayacaktır. 2. nesil üzerinde kadar veri değilse, bunun en az etkisi vardır. Ancak 2. nesil büyükse, birçok 2. nesil GC'ler tetiklenen durumunda performans sorunlarına neden olabilir. Birçok büyük nesneler çok geçici temeline göre ayrılır ve büyük SOH varsa GC'ler yapılması çok fazla zaman harcama. Ayrıca, ayırma maliyet gerçekten ayırma ve izin vererek gerçekten büyük nesnelerin Git tutmak ekleyebilirsiniz.

- Başvuru türleri öğelerle dizi.

   Çok büyük nesneler üzerinde LOH genellikle (gerçekten büyük bir örnek nesne sağlamak için çok nadir) dizidir. Dizi öğeleri ise isteğe bağlı olarak başvuru-zengin, öğeleri değilseniz, mevcut olmayan bir maliyet oluşturur başvuru zengin. Öğe tüm başvuruları içermiyorsa, atık toplayıcı dizi boyunca hiç gitmek gerekmez. Bir ikili ağacı düğümleri depolamak için bir dizi kullanırsanız, örneğin, uygulamak için tek bir düğümün sağ ve sol düğüm gerçek düğümleri tarafından başvurmak için yoludur:

   ```csharp
   class Node
   {
      Data d;
      Node left;
      Node right;
   };

   Node[] binary_tr = new Node [num_nodes];
   ```

   Varsa `num_nodes` olan öğesi başına en az iki başvuru gitmesi büyük, atık toplayıcı gerekiyor. Sağ ve sol düğümler dizinini depolamak için alternatif bir yaklaşım şöyledir:

   ```csharp
   class Node
   {
      Data d;
      uint left_index;
      uint right_index;
   } ;
   ```

   Sol düğümün verileri olarak başvuran yerine `left.d`, olarak başvuran `binary_tr[left_index].d`. Ve atık toplayıcı sol ve sağ düğüm için tüm başvuruları bakmak gerekmez.

Üç dışında ilk iki genellikle üçüncü daha önemli faktörlerdir. Bu nedenle, geçici olanları ayırma yerine yeniden büyük nesneler havuzu ayırma öneririz. 

## <a name="collecting-performance-data-for-the-loh"></a>LOH için performans verilerini toplama

Belirli bir alan için performans verilerini toplama önce aşağıdakileri yapmış olduğunuz:

1. Bu alanında aramanız gereken kanıt bulundu.

1. Gördüğünüz performans sorunu açıklayan, herhangi bir şey bulmadan bildiğiniz diğer alanlarına tükendi.

Blog bakın [bir çözüm bulmak denemeden önce sorunu anlamak](https://blogs.msdn.microsoft.com/maoni/2006/09/01/understand-the-problem-before-you-try-to-find-a-solution/) bellek ve CPU temelleri hakkında daha fazla bilgi için.

LOH performans verilerini toplamak için aşağıdaki araçları kullanabilirsiniz:

- [.NET CLR bellek performansı sayaçları](#net-clr-memory-performance-counters)

- [ETW olayları](#etw-events)

- [Hata ayıklayıcı](#a-debugger)

### <a name="net-clr-memory-performance-counters"></a>.NET CLR bellek performans sayaçları

Bu performans sayaçlarını performans sorunları incelemeye bir iyi ilk adımı genellikle olan (kullanmanızı öneririz, ancak [ETW olayları](#etw)). Şekil 4'te gösterildiği gibi istediğiniz sayaçları ekleyerek Performans İzleyicisi'ni yapılandırın. LOH için uygun olan ve güçlüklerdir:

- **\# Gen 2 koleksiyonları**

   2. nesil GC'ler işlem başlatıldığından bu yana gerçekleşen sayısını görüntüler. (Tam atık toplama olarak da bilinir) 2. nesil koleksiyonunun sonuna sayaç artırılır. Bu sayaç gözlenen son değeri görüntüler.

- **Büyük nesne yığın boyutu**

   Geçerli boyut boş alanı, LOH dahil olmak üzere bayt cinsinden görüntüler. Bu sayaç her ayırma değil, bir atık toplama işleminin sonunda güncelleştirilir.

Performans İzleyicisi (perfmon.exe) performans sayaçları aramak için genel bir yoludur. İlgilendiğiniz işlemler için ilginç sayaç eklemek için "Sayaç Ekle" kullanın. Şekil 4'te gösterildiği gibi bir günlük dosyasına performans sayacı verilerini kaydedebilirsiniz.

![Şekil 4: performans sayaçları ekleniyor.](media/loh/perfcounter.png)    
Şekil 4: 2. nesil GC sonra LOH

Performans sayaçları de bir program aracılığıyla sorgulanabilir. Birçok kişi bunları kendi rutin sınama işleminin bir parçası olarak bu şekilde toplayın. Sıra dışıdır olan değerleri sayaçlarıyla nokta, bunlar başka yöntemler ile araştırmaya yardımcı olmak için ayrıntılı veri almak için kullanın.

> [!NOTE]
> ETW kadar daha zengin bilgi sağladığından, ETW olayları performans yerine kullanılacak sayaçları olduğunu, öneririz.

### <a name="etw"></a>ETW

Çöp toplayıcı ETW olayları öbek ne yaptığını anlamanıza yardımcı olması için zengin bir dizi sağlar ve neden. Aşağıdaki blog gönderileri toplamak ve GC olayları ETW ile anlamak nasıl göster:

- [GC ETW olayları - 1 ](http://blogs.msdn.com/b/maoni/archive/2014/12/22/gc-etw-events.aspx)

- [GC ETW olayları - 2](http://blogs.msdn.com/b/maoni/archive/2014/12/25/gc-etw-events-2.aspx)

- [GC ETW olayları - 3](http://blogs.msdn.com/b/maoni/archive/2014/12/25/gc-etw-events-3.aspx) 

- [GC ETW olayları - 4](http://blogs.msdn.com/b/maoni/archive/2014/12/30/gc-etw-events-4.aspx)

Aşırı nesil 2 GC'ler tarafından geçici LOH ayırmaları nedeni belirlemek için GC'ler için tetikleyici neden sütununa bakın. Yalnızca geçici büyük nesneler tarafından ayrılan basit bir test için ETW olaylarına aşağıdaki bilgi toplayabilirsiniz [PerfView](https://www.microsoft.com/download/details.aspx?id=28567) komut satırı:

```console
perfview /GCCollectOnly /AcceptEULA /nogui collect
```

Sonuç şöyle olur:
 
![Şekil 5: ETW olayları PerfView kullanarak inceleniyor](media/loh/perfview.png)  
Şekil 5: PerfView kullanılarak gösterilen ETW olayları

Gördüğünüz gibi 2. nesil GC'ler tüm GC'ler olan ve tüm büyük nesne ayırma bu GC tetiklenen anlamına gelir AllocLarge tarafından tetiklenir. Bu ayırmaları geçici olduğunu biliyoruz çünkü **LOH hayatta kalma oranı %** sütun %1 söyler.

Bu büyük nesneler ayrılan size ek ETW olayları toplayabilir. Aşağıdaki komut satırı:

```console
perfview /GCOnly /AcceptEULA /nogui collect
```

yaklaşık her 100 k değerinde ayırmaları harekete AllocationTick olay toplar. Diğer bir deyişle, her zaman büyük nesne ayrılmış bir olay tetiklenir. Ayrılmış büyük nesneleri callstacks Göster GC yığın ayırma görünümler birini sonra arayabilirsiniz:
 
![Şekil 6: Bir GC yığın ayırma görünümü](media/loh/perfview2.png)  
Şekil 6: Bir GC yığın ayırma görünümü
 
Gördüğünüz gibi yalnızca büyük nesneleri ayırır çok basit bir sınama budur kendi `Main` yöntemi.

### <a name="a-debugger"></a>Hata ayıklayıcı

Sahip olduğunuz şey bir bellek dökümü ve nesneleri gerçekten üzerinde LOH nelerdir aramak gereken, kullanabileceğiniz [SoS hata ayıklayıcı uzantısı](http://msdn2.microsoft.com/ms404370.aspx) .NET tarafından sağlanan. 

> [!NOTE]
> Bu bölümde belirtilen hata ayıklama komutları için geçerli olan [Windows hata ayıklayıcıları](http://www.microsoft.com/whdc/devtools/debugging/default.mspx).

Aşağıdaki LOH çözümleme gelen örnek çıkış şunları gösterir:

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

LOH yığın boyutudur (16,754,224 + 16,699,288 + 16,284,504) = 49,738,016 bayt. Adresleri 023e1000 ve 033db630 arasında 8,008,736 bayt dizisi tarafından kapladığı <xref:System.Object?displayProperty=fullName> nesneleri 6,663,696 bayt dizisi tarafından kapladığı <xref:System.Byte?displayProperty=nameWithType> nesneleri ve 2,081,792 bayt tarafından boş alanı dolu.

Bazı durumlarda, hata ayıklayıcı LOH toplam boyutu 85. 000 bayt'tan küçük olduğunu gösterir. Çalışma zamanı kendisini geniş bir nesne daha küçük olan bazı nesneler ayrılacak LOH kullandığından bu gerçekleşir.

LOH sıkıştırılmış değil, bazen LOH parçalanma bir kaynak olarak thoought olmasıdır. Parçalanma anlamına gelir:

- Yönetilen nesneler arasında boş alan miktarı tarafından gösterilen Yönetilen yığın parçalanma. SoS içinde `!dumpheap –type Free` komutu, yönetilen nesneler arasında boş alan miktarını görüntüler.

- Bellek sanal bellek (VM) adres alanının parçalanması olarak işaretli `MEM_FREE`. İçinde windbg çeşitli hata ayıklayıcı komutlarını kullanarak elde edebilirsiniz.

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

Sık sık yeni edinmeye atık toplayıcı yığın kesimleri OS yönetilen ve boş olanları işletim sistemine geri yayın gerektiren geçici büyük nesneler nedeni VM parçalanma görmek için daha yaygın bir durumdur.

LOH VM parçalanma neden olup olmadığını doğrulamak için bir kesme noktası ayarlayabilirsiniz [VirtualAlloc](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx) ve [VirtualFree](https://msdn.microsoft.com/library/windows/desktop/aa366892(v=vs.85).aspx) kimin çağrı görmek için. Örneğin, kimin OS 8MBB büyük sanal bellek parçalara ayırmaya çalıştığını görmek için böyle bir kesme noktası ayarlayabilirsiniz:

```console
bp kernel32!virtualalloc "j (dwo(@esp+8)>800000) 'kb';'g'"
```

Bu komut ayıklayıcıya keser ve çağrı yığını eksikse gösterir [VirtualAlloc](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx) bir ayırma boyutu (0x800000) 8 MB'den büyük olarak adlandırılır.

CLR 2.0 eklenen adlı bir özelliği *VM Hoarding* , scenarious için yararlı olabilir burada kesim (yığın nesnesi büyük ve küçük üzerinde de dahil olmak üzere) sık edinilen ve yayımlanan. Adlı bir başlangıç bayrak belirttiğiniz VM Hoarding belirtmek için `STARTUP_HOARD_GC_VM` barındırma API aracılığıyla. İşletim sistemi boş segmentlere geri serbest bırakma, yerine CLR bu kesimler belleği decommits ve bunları bir bekleme listesine koyar. (CLR bu çok büyük kesimine yönelik işlemi gerçekleştirmeyen unutmayın.) CLR daha sonra yeni segment isteklerini karşılamak için bu kesimler kullanır. Kadar büyük olan bir bulabilirsiniz, uygulamanızın yeni bir segment gerektiğini başlattığınızda bekleme bu listeden bir CLR kullanır.

VM hoarding, bunlar zaten, yetersiz bellek özel durumları önlemek için bu sistemde çalışan baskın uygulamaların bazı sunucu uygulamaları gibi edinilen kesimleri üzerine tutmak istediğiniz uygulamalar için de yararlıdır.

Olgunluğa bellek kullanımı, uygulamanızın sağlamak için bu özelliği kullandığınızda, dikkatle uygulamanızı sınamanızı öneririz.
