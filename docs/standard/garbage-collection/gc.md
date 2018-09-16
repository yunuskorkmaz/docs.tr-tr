---
title: Otomatik bellek yönetimi ve çöp toplama
description: Otomatik bellek yönetimi ortak dil çalışma zamanı yönetilen yürütme sırasında sağladığı hizmetlerden biridir öğrenin.
ms.date: 07/22/2016
ms.technology: dotnet-standard
ms.assetid: d095b0b6-2454-4e23-80b4-c9e8a447116c
ms.openlocfilehash: 8046cb744dccaf512208d517c243640820efce8e
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45685770"
---
# <a name="automatic-memory-management-and-garbage-collection"></a>Otomatik bellek yönetimi ve çöp toplama

Otomatik bellek yönetimi, ortak dil çalışma zamanı yönetilen yürütme sırasında sağladığı hizmetlerden biridir. Ortak dil çalışma zamanının atık toplayıcısı sağlanmasını ve bir uygulama için belleğin ayrılmasını yönetir. Geliştiriciler için bu, yönetilen uygulamalar geliştirirken bellek yönetimi görevleri gerçekleştirmek için kod yazmaya gerek olmadığı anlamına gelir. Otomatik bellek yönetimi, bir nesneyi serbest bırakmayı unutarak bir bellek sızıntısına neden olmak veya daha önce serbest bırakılmış bir nesnenin belleğine erişmeye çalışmak gibi yaygın sorunları ortadan kaldırabilir. Bu bölümde, atık toplayıcının belleği nasıl ayırdığı ve serbest bıraktığı açıklanmaktadır.

## <a name="allocating-memory"></a>Bellek Ayırma

Yeni bir işlem başlattığınızda, çalışma zamanı işlem için adres bölgesine bitişik bir adres alanı ayırır. Bu ayrılmış adres alanına yönetilen yığın denir. Yönetilen yığın, yığın içinde sıradaki nesnenin nereye ayrılacağını belirten bir işaretçi tutar. Başlangıçta, bu işaretçi yönetilen yığının taban adresi olarak ayarlanır. Tüm başvuru türleri yönetilen yığında ayrılır. Bir uygulama ilk referans türünü oluşturduğunda, türe yönelik bellek, yönetilen yığının taban adresinde ayrılır. Uygulama bir sonraki nesneyi oluşturduğunda, atık toplayıcı bunun için ilk nesnenin hemen ardındaki adres alanında bellek ayırır. Kullanılabilir adres alanı olduğu sürece, atık toplayıcı yeni nesnelere bu şekilde bellek ayırmaya devam eder.

Yönetilen yığından bellek ayırmak, yönetilmeyen bellek ayrımından daha hızlıdır. Çalışma zamanı bir nesneye bellek ayırmak için bir işaretçiye bir değer eklediği için, neredeyse yığından bellek ayırma kadar hızlıdır. Ek olarak, art arda ayrılan nesneler yönetilen yığında bitişik bir biçimde tutulduklarından, uygulama nesnelere çok hızlı bir şekilde erişebilir.

## <a name="releasing-memory"></a>Bellek Serbest Bırakma

Atık toplayıcısının optimizasyon altyapısı, yapılan ayrımlara göre bir toplama işlemini gerçekleştirmek için en iyi zamanı belirler. Atık toplayıcı bir toplama gerçekleştirdiğinde, uygulama tarafından artık kullanılmayan nesnelere ayrılan belleği serbest bırakır. Uygulamanın köklerini inceleyerek hangi nesnelerin artık kullanılmadığını belirler. Her uygulamanın bir kök kümesi vardır. Her kök yönetilen yığındaki bir nesneye başvurur veya null olarak ayarlanır. Bir uygulamanın köklerini statik alanlar, yerel değişkenleri ve parametreleri bir iş parçacığının yığınındaki içerir ve CPU yazmaçlarını içerir. Çöp toplayıcı, just-in-time (JIT) derleyici ve çalışma zamanı etkin kökler listesine erişimi vardır. Bu listeyi kullanarak bir uygulamanın köklerini inceler, ve bu esnada köklerden erişilebilen tüm nesneleri içeren bir grafik oluşturur.

Grafta bulunmayan nesnelere uygulamanın köklerinden ulaşılamaz. Atık toplayıcı erişilemeyen nesneleri atık olarak görür ve onlar için ayrılan belleği serbest bırakır. Bir toplama sırasında, atık toplayıcı yönetilen yığını inceleyerek erişilemeyen nesneler tarafından kullanılan adres alanı bloklarını arar. Erişilemeyen nesneleri keşfettikçe, bir bellek kopyalama işleviyle bellekteki erişilebilir nesneleri sıkıştırır ve bu sayede, erişilemeyen nesnelere ayrılan adres alanlarını serbest bırakır. Erişilebilir nesneler için bellek sıkıştırıldıktan sonra atık toplayıcı gerekli işaretçi düzeltmelerini yaparak uygulamanın köklerinin nesnelerin yeni konumlarına işaret etmesini sağlar. Ayrıca yönetilen yığının işaretçisini erişilebilen son nesnenin sonuna konumlandırır. Belleğin yalnızca bir toplama işlemi tarafından büyük miktarda erişilemeyen nesne keşfedilirse sıkıştırıldığına dikkat edin. Yönetilen bellekteki tüm nesneler bir toplamadan sonra kalmaya devam ederse, bellek sıkıştırmaya gerek yoktur.

Performansı artırmak açısından, çalışma zamanı büyük nesneler için ayrı bir yığında bellek ayırır. Atık toplayıcı, büyük nesnelerin belleğini otomatik olarak serbest bırakır. Ancak, büyük nesnelerin bellekte taşınmasını önlemek amacıyla, bu bellek sıkıştırılmaz.

## <a name="generations-and-performance"></a>Nesiller ve Performans

Atık toplayıcının performansını optimize etmek için, yönetilen yığın üç nesle ayrılır: 0, 1 ve 2. Çalışma zamanının atık toplama algoritması, bilgisayar yazılımı endüstrisinin atık toplama şemaları ile deneyler gerçekleştirerek doğru olduğunu anladığı birkaç genellemeyi temel alır. İlk olarak, yönetilen yığının tamamı yerine yönetilen yığının bir bölümü için belleği sıkıştırmak daha hızlıdır. İkinci olarak, yeni nesneler daha kısa, eski nesnelerse daha uzun ömre sahip olur. Son olarak, yeni nesneler birbirleriyle ilişkili olma eğilimindedir ve uygulama tarafından yaklaşık olarak aynı zamanda erişilirler.

Çalışma zamanının atık toplayıcısı, yeni nesneleri nesil 0'da tutar. Uygulama ömrünün başlarında oluşturulan ve toplamalardan sonra varlığını sürdüren nesneler yükseltilerek nesil 1 ve 2'de tutulur. Nesne yükseltme işlemi bu konunun ilerleyen bölümlerinde açıklanmıştır. Yönetilen yığının tamamındansa bir bölümünü sıkıştırmak daha hızlı olduğundan, bu yöntem atık toplayıcının her toplama işleminde tüm yönetilen yığın için belleği serbest bırakmasındansa yalnızca belirli bir nesildeki belleği serbest bırakmasına olanak sağlar.

Gerçekte, atık toplayıcı nesil 0 dolduğunda bir toplama işlemi gerçekleştirir. Bir uygulama nesil 0 doluyken yeni bir nesne oluşturmayı denerse, atık toplayıcı nesil 0 içinde nesneye ayrılabilecek hiçbir adres alanı kalmadığını görür. Atık toplayıcı nesne için nesil 0'da adres alanı oluşturma amacıyla bir toplama işlemi gerçekleştirir. Atık toplayıcı, yönetilen yığındaki tüm nesneler yerine nesil 0'daki nesneleri inceleyerek başlar. Bu en etkili yaklaşımdır, çünkü yeni nesneler daha kısa ömre sahip olmaya meyillidir ve bir toplama işlemi gerçekleştirildiğinde nesil 0'daki nesnelerin pek çoğunun uygulama tarafından artık kullanılmıyor olması beklenir. Ek olarak, yalnızca nesil 0'da gerçekleştirilen bir toplama işlemi, genellikle uygulamanın yeni nesneler oluşturmasına yetecek kadar belleğin geri kazanılmasını sağlar.

Atık toplayıcı nesil 0 bir toplama işlemi gerçekleştirdikten sonra bunu erişilebilir nesneler için bellek açıklandığı şekilde düzenler [bellek serbest bırakma](#releasing-memory) bu konuda daha önce. Atık toplayıcı ardından bu nesneleri yükseltir ve yönetilen yığının bu bölümünü nesil 1 olarak değerlendirir. Toplama işleminden sonra varlığını sürdüren nesneler daha uzun ömre sahip olmaya eğilimli olduklarından, bunları daha yüksek bir nesle yükseltmek mantıklıdır. Sonuç olarak, atık toplayıcısı nesil 0'da gerçekleştirdiği her toplama işlemine karşılık olarak nesil 1 ve 2'deki nesneleri yeniden gözden geçirmek zorunda kalmaz.

Atık toplayıcısı nesil 0 için ilk toplama işlemini gerçekleştirdikten ve erişilebilen nesneleri nesil 1'e yükselttikten sonra, yönetilen yığının kalanını nesil 0 olarak değerlendirir. Nesil 0 dolana ve başka bir toplama işlemi gerçekleştirmek gerekene kadar yeni nesneler için nesil 0'da bellek ayırmaya devam eder. Bu noktada, atık toplayıcının optimizasyon motoru, önceki nesillerdeki nesnelerin incelenmesinin gerekip gerekmediğini belirler. Örneğin, nesil 0'da gerçekleştirilen bir toplama işlemi, uygulamanın yeni nesne oluşturma işlemini başarıyla tamamlayabilmesi için yeterli miktarda bellek geri kazanamazsa, atık toplayıcı önce nesil 1, ardından da nesil 2 için bir toplama işlemi gerçekleştirebilir. Eğer bu yeterince belleğin geri kazanılmasını sağlamazsa, atık toplayıcı nesil 2, 1 ve 0 için bir toplama işlemi gerçekleştirebilir. Her toplama işleminden sonra atık toplayıcı nesil 0 içindeki erişilebilir nesneleri sıkıştırıp nesil 1'e yükseltir. Nesil 1'de toplama işlemlerinden sonra varlığına devam eden nesneler nesil 2'ye yükselir. Atık toplayıcı yalnızca üç nesil desteklediği için, nesil 2'de bir toplama işleminden sonra varlığını sürdüren nesneler gelecekteki bir toplama işleminde erişilemez olarak belirlenene kadar nesil 2 içinde kalmaya devam eder.

## <a name="releasing-memory-for-unmanaged-resources"></a>Yönetilmeyen Kaynaklar için Bellek Serbest Bırakma

Uygulamanızın oluşturduğu nesnelerin çoğu için, gerekli bellek yönetimi görevlerini otomatik olarak gerçekleştirilmesi konusunda atık toplayıcıya güvenebilirsiniz. Ancak, yönetilmeyen kaynakların açıkça temizlenmesi gerekir. Yönetilmeyen kaynakların en yaygın türü, bir dosya işleyicisi, pencere işleyicisi veya ağ bağlantısı gibi işletim sistemi kaynağını sarmalayan bir nesnedir. Atık toplayıcı yönetilmeyen bir kaynağı sarmalayan yönetilen bir nesnenin ömrünü takip edebilse de, kaynağı temizlemek için gerekli olan özel bilgilere sahip değildir. Yönetilmeyen bir kaynağı sarmalayan bir nesne oluşturduğunuzda, genel bir yönetilmeyen kaynağı temizlemek için gereken kodu sağlamanız önerilir `Dispose` yöntemi. Sağlayarak bir `Dispose` yöntemi, nesnenizin kullanıcılarının nesneyle işiniz bittiğinde açıkça belleği boşaltmak etkinleştirin. Yönetilmeyen bir kaynağı sarmalayan bir nesne kullandığınızda, bilmeniz `Dispose` ve gerektiğinde çağırmalısınız. Yönetilmeyen kaynakları ve uygulamak için bir tasarım düzeni örneği temizleme hakkında daha fazla bilgi için `Dispose`, bkz: [.NET çöp toplamada](index.md).

## <a name="see-also"></a>Ayrıca bkz.

- [System.GC](xref:System.GC)
- [. NET'te çöp toplama](index.md)
