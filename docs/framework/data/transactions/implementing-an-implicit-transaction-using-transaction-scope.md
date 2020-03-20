---
title: İşlem Kapsamı Kullanarak Örtük İşlem Uygulama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49d1706a-1e0c-4c85-9704-75c908372eb9
ms.openlocfilehash: 33b51cf26a35bbdda70582d86db6ac39c22597da
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174400"
---
# <a name="implementing-an-implicit-transaction-using-transaction-scope"></a>İşlem Kapsamı Kullanarak Örtük İşlem Uygulama
Sınıf, <xref:System.Transactions.TransactionScope> hareketin kendisiyle etkileşimkurmanızı gerektirmeden, bir kod bloğunu bir hareketle ilgili olarak işaretlemenin basit bir yolunu sağlar. Hareket kapsamı ortam işlemini otomatik olarak seçebilir ve yönetebilir. Kullanım kolaylığı ve verimliliği nedeniyle, bir işlem uygulaması <xref:System.Transactions.TransactionScope> geliştirirken sınıfı kullanmanız önerilir.  
  
 Ayrıca, kaynakları açıkça hareketle kaydolmanız gerekmez. Herhangi <xref:System.Transactions> bir kaynak yöneticisi (SQL Server 2005 gibi) kapsam tarafından oluşturulan bir ortam hareketinin varlığını algılayabilir ve otomatik olarak kaydolabilir.  
  
## <a name="creating-a-transaction-scope"></a>Hareket kapsamı oluşturma  
 Aşağıdaki örnek, bir basit kullanımını gösterir <xref:System.Transactions.TransactionScope> sınıfı.  
  
 [!code-csharp[TransactionScope#1](../../../../samples/snippets/csharp/VS_Snippets_Remoting/TransactionScope/cs/ScopeWithSQL.cs#1)]
 [!code-vb[TransactionScope#1](../../../../samples/snippets/visualbasic/VS_Snippets_Remoting/TransactionScope/vb/ScopeWithSQL.vb#1)]  
  
 Yeni <xref:System.Transactions.TransactionScope> bir nesne oluşturduğunuzda hareket kapsamı başlatılır.  Kod örneğinde gösterildiği gibi, bir `using` deyimle kapsam oluşturmanız önerilir. `using` İfade c# ve Visual Basic hem de mevcuttur `try`ve bir gibi çalışır ... `finally` kapsamın düzgün bir şekilde atıldığından emin olmak için blok.  
  
 <xref:System.Transactions.TransactionScope>Anında işlem yöneticisi hangi işlemin katılacağını belirler. Belirlendikten sonra, kapsam her zaman bu işlemde katılır. Karar iki faktöre dayanır: ortam işleminin mevcut olup olmadığı `TransactionScopeOption` ve oluşturucudaki parametrenin değeri. Ortam hareketi, kodunuzun yürütüldettiği harekettir. <xref:System.Transactions.Transaction> Sınıfın statik <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType> özelliğini arayarak ortam hareketine başvuru alabilirsiniz. Bu parametrenin nasıl kullanıldığı hakkında daha fazla bilgi için, bu konunun [TransactionScopeOption](#ManageTxFlow) bölümünü kullanarak Yönetim hareket akışına bakın.  
  
## <a name="completing-a-transaction-scope"></a>Hareket kapsamını tamamlama  
 Uygulamanız bir işlemde gerçekleştirmek istediği tüm işi tamamladığında, <xref:System.Transactions.TransactionScope.Complete%2A?displayProperty=nameWIthType> işlem yöneticisine hareketi gerçekleştirmenin kabul edilebilir olduğunu bildirmek için yöntemi yalnızca bir kez aramalısınız. Bu <xref:System.Transactions.TransactionScope.Complete%2A> `using` blokta son ifade olarak arama koymak için çok iyi bir uygulamadır.  
  
 İşlem yöneticisi bunu bir sistem hatası veya işlem kapsamında atılan bir özel durum olarak yorumladığı için, bu yöntemin çağrılmaması hareketi iptal eder. Ancak, bu yöntemi çağırmak, işlemin solunan bir söz olduğunu garanti etmez. Bu yalnızca işlem yöneticisine durumunuzu bildirmenin bir yoludur. <xref:System.Transactions.TransactionScope.Complete%2A> Yöntemi aradıktan sonra, <xref:System.Transactions.Transaction.Current%2A> özelliği kullanarak ortam hareketine artık erişemezsiniz ve bunu yapmaya çalışmak bir özel durum atılmasına neden olur.  
  
 <xref:System.Transactions.TransactionScope> Nesne hareketi başlangıçta oluşturduysa, hareket yöneticisi tarafından hareketi gerçekleştirmenin gerçek işi `using` bloktaki son kod satırından sonra gerçekleşir. İşlemi oluşturmadıysa, <xref:System.Transactions.CommittableTransaction.Commit%2A> <xref:System.Transactions.CommittableTransaction> nesnenin sahibi tarafından çağrıldığında commit oluşur. Bu noktada işlem yöneticisi kaynak yöneticilerini çağırır ve yöntemin <xref:System.Transactions.TransactionScope.Complete%2A> <xref:System.Transactions.TransactionScope> nesneye çağrılıp çağrılmadığına bağlı olarak kaynak yöneticilerini çağırır ve onları işleme veya geri alma konusunda bilgilendirir.  
  
 Deyim, `using` bir özel <xref:System.Transactions.TransactionScope.Dispose%2A> durum <xref:System.Transactions.TransactionScope> oluşsa bile nesnenin yönteminin çağrılmasını sağlar. Yöntem, <xref:System.Transactions.TransactionScope.Dispose%2A> hareket kapsamının sonunu işaretler. Bu yöntemi aradıktan sonra oluşan özel durumlar hareketi etkilemeyebilir. Bu yöntem, ortam işlemini önceki durumuna da geri yükler.  
  
 Kapsam <xref:System.Transactions.TransactionAbortedException> hareketi oluşturursa ve hareket iptal edilirse a atılır. Hareket <xref:System.Transactions.TransactionInDoubtException> yöneticisi Commit kararına ulaşamıyorsa a atılır. Hareket işlenirse özel durum atılmaz.  
  
## <a name="rolling-back-a-transaction"></a>Bir hareketi geri alma  
 Bir hareketi geri almak istiyorsanız, <xref:System.Transactions.TransactionScope.Complete%2A> yöntemin işlem kapsamı içinde çağrılmaması gerekir. Örneğin, kapsam içinde bir özel durum. Katıldığı işlem geri alınır.  
  
## <a name="managing-transaction-flow-using-transactionscopeoption"></a><a name="ManageTxFlow"></a>TransactionScopeOption kullanarak işlem akışını yönetme  
 İşlem kapsamı, aşağıdaki örnekte olduğu gibi, <xref:System.Transactions.TransactionScope> `RootMethod` kendi kapsamını kullanan bir yöntem içinden a kullanan bir yöntem çağırarak iç içe olabilir,  
  
```csharp  
void RootMethod()
{
    using(TransactionScope scope = new TransactionScope())
    {
        /* Perform transactional work here */
        SomeMethod();
        scope.Complete();
    }
}

void SomeMethod()
{
    using(TransactionScope scope = new TransactionScope())
    {
        /* Perform transactional work here */
        scope.Complete();
    }
}
```  
  
 En çok işlem kapsamı kök kapsamı olarak adlandırılır.  
  
 Sınıf, <xref:System.Transactions.TransactionScope> kapsamın işlem davranışını tanımlayan türün <xref:System.Transactions.TransactionScopeOption>numaralandırmasını kabul eden birkaç aşırı yüklü oluşturucu sağlar.  
  
 Bir <xref:System.Transactions.TransactionScope> nesnenin üç seçenek vardır:  
  
- Ortam işlemine katılın veya yoksa yeni bir işlem oluşturun.  
  
- Yeni bir kök kapsam, yani, yeni bir işlem başlatmak ve bu işlem kendi kapsamı içinde yeni ortam hareketi olmak olun.  
  
- Bir işlemde yer almamak. Sonuç olarak ortam hareketi yoktur.  
  
 Kapsam <xref:System.Transactions.TransactionScopeOption.Required>ile anında ve ortam hareketi varsa, kapsam bu hareketi birleştirir. Diğer taraftan, ortam hareketi yoksa, kapsam yeni bir işlem oluşturur ve kök kapsam haline gelir. Varsayılan değer budur. Kullanıldığında, <xref:System.Transactions.TransactionScopeOption.Required> kapsam içindeki kodun kök olsun veya sadece ortam işlemine katılarak farklı davranması gerekmez. Her iki durumda da aynı şekilde çalışması.  
  
 Kapsamı ile örneği varsa <xref:System.Transactions.TransactionScopeOption.RequiresNew>, her zaman bir kök kapsam olur. Yeni bir işlem başlatır ve hareketi kapsam içindeki yeni ortam hareketi olur.  
  
 Kapsam, <xref:System.Transactions.TransactionScopeOption.Suppress>ortam hareketinin mevcut olup olmadığına bakılmaksızın hiçbir zaman bir işlemde yer almaz. Bu değerle anında birleştirilmiş bir `null` kapsam, ortam hareketi olarak her zaman vardır.  
  
 Yukarıdaki seçenekleri aşağıdaki tabloda özetlenmiştir.  
  
|TransactionScopeOption|Ortam İşlemi|Kapsam bölümü alır|  
|----------------------------|-------------------------|-----------------------------|  
|Gerekli|Hayır|Yeni İşlem (kök olacak)|  
|Yeni gerektirir|Hayır|Yeni İşlem (kök olacak)|  
|Önle|Hayır|İşlem Yok|  
|Gerekli|Evet|Ortam İşlemi|  
|Yeni gerektirir|Evet|Yeni İşlem (kök olacak)|  
|Önle|Evet|İşlem Yok|  
  
 Bir <xref:System.Transactions.TransactionScope> nesne varolan bir ortam hareketine katıldığında, kapsam nesnesinin atılması, kapsam hareketi iptal etmediği sürece hareketi sonlandıramaz. Ortam hareketi bir kök kapsamı tarafından oluşturulduysa, yalnızca kök kapsamı atıldığında, hareket <xref:System.Transactions.CommittableTransaction.Commit%2A> çağrıldı. Hareket el ile oluşturulduysa, hareket iptal edildiğinde veya oluşturucusu tarafından işlendiğinde sona erer.  
  
 Aşağıdaki örnekte gösterildiği bir <xref:System.Transactions.TransactionScope> üç iç içe kapsamlı nesneler, farklı bir her örneklenen oluşturan nesne <xref:System.Transactions.TransactionScopeOption> değeri.  
  
```csharp  
using(TransactionScope scope1 = new TransactionScope())
//Default is Required
{
    using(TransactionScope scope2 = new TransactionScope(TransactionScopeOption.Required))
    {
        //...
    }

    using(TransactionScope scope3 = new TransactionScope(TransactionScopeOption.RequiresNew))
    {
        //...  
    }
  
    using(TransactionScope scope4 = new TransactionScope(TransactionScopeOption.Suppress))
    {
        //...  
    }
}
```  
  
 Örnek, herhangi bir ortam hareketi oluşturmadan bir kod`scope1`bloğu <xref:System.Transactions.TransactionScopeOption.Required>gösterir ( ) ile . `scope1` Kapsam, yeni bir hareket (Hareket A) oluşturur ve Hareket A'yı ortam hareketi yapar gibi bir kök kapsamdır. `Scope1`Daha sonra her farklı bir ile üç daha fazla nesne oluşturur <xref:System.Transactions.TransactionScopeOption> değeri. Örneğin, `scope2` 'ile <xref:System.Transactions.TransactionScopeOption.Required>oluşturulur ve bir ortam hareketi olduğundan, '' tarafından `scope1`oluşturulan ilk işlem birleştirir. Yeni `scope3` bir işlemin kök kapsamı olduğunu ve `scope4` ortam hareketi olmadığını unutmayın.  
  
 Değerini varsayılan ve en sık kullanılan olsa da <xref:System.Transactions.TransactionScopeOption> olan <xref:System.Transactions.TransactionScopeOption.Required>, her diğer değerlerinin benzersiz amacı vardır.  

### <a name="non-transactional-code-inside-a-transaction-scope"></a>Hareket kapsamı içinde işlem kodu olmayan

 <xref:System.Transactions.TransactionScopeOption.Suppress>kod bölümü tarafından gerçekleştirilen işlemleri korumak istediğinizde ve işlemler başarısız olursa ortam işlemini iptal etmek istemediğiniz zaman yararlıdır. Örneğin, günlüğe kaydetme veya denetleme işlemleri gerçekleştirmek istediğinizde veya ortam işleminizin taahhüt edilip edilmediğine veya iptal edilmediğine bakılmaksızın olayları abonelere yayınlamak istediğinizde. Bu değer, aşağıdaki örnekte gösterildiği gibi, bir işlem kapsamı içinde işlem dışı bir kod bölümüne sahip olmak sağlar.  
  
```csharp  
using(TransactionScope scope1 = new TransactionScope())
{
    try
    {
        //Start of non-transactional section
        using(TransactionScope scope2 = new
            TransactionScope(TransactionScopeOption.Suppress))  
        {  
            //Do non-transactional work here  
        }  
        //Restores ambient transaction here
   }
   catch {}  
   //Rest of scope1
}
```  
  
### <a name="voting-inside-a-nested-scope"></a>İç içe bir kapsam içinde oylama  
 İç içe bir kapsam kök kapsamının ortam hareketine <xref:System.Transactions.TransactionScope.Complete%2A> katılabilse de, iç içe olan kapsamdaki aramanın kök kapsamı üzerinde hiçbir etkisi yoktur. Yalnızca, kök kapsamdan işlem için son iç içe geçen kapsama kadar tüm kapsamlar oylanırsa, işlem işlenir. Ortam <xref:System.Transactions.TransactionScope.Complete%2A> hareketi hemen iptal edilince, iç içe bir kapsamda aramamak kök kapsamı etkileyecektir.  
  
## <a name="setting-the-transactionscope-timeout"></a>TransactionScope zaman ayarı  
 Aşırı yüklü yapıcıların bazıları, <xref:System.Transactions.TransactionScope> hareketin zaman <xref:System.TimeSpan>aşımını denetlemek için kullanılan bir tür değerini kabul eder. Sıfır olarak ayarlanmış bir zaman aşımı sonsuz bir zaman aşımı anlamına gelir. Sonsuz zaman aşımı, kodunuzda adım atarak iş mantığınızdaki bir sorunu yalıtmak istediğinizde ve hatayı ayıklama işleminin sorunu bulmaya çalışırken zaman dışarı etmesini istemiyorsanız, hata ayıklama için çoğunlukla hata ayıklama için yararlıdır. İşlem kilitlenmelerine karşı korumaları geçersiz kıldığı için, diğer tüm durumlarda sonsuz zaman kaybı değerini kullanırken son derece dikkatli olun.  
  
 Genellikle ayarlanabilir <xref:System.Transactions.TransactionScope> zaman aşımına uğramak üzere iki durumda da varsayılan dışındaki değerler. İlki, uygulamanızın iptal edilen hareketleri işleme şeklini test etmek istediğiniz geliştirme sırasındadır. Zaman aşışını küçük bir değere (bir milisaniye gibi) ayarlayarak, işleminizin başarısız olması için sorun alabilirsiniz ve böylece hata işleme kodunuzu gözlemleyebilirsiniz. Kapsam içinde kaynak talebi, söz konusu kilitlenmeleri kaynaklanan düşünüyorsanız, varsayılan zaman aşımı değerinden bir değere ayarlamanız ikinci durumdur. Bu durumda, hareketi mümkün olan en kısa sürede iptal etmek ve varsayılan zaman aşımısüresinin dolmasını beklememek istiyorsunuz.  
  
 Bir kapsam ortam hareketine katıldığında ancak ortam hareketinin ayarlandığından daha küçük bir zaman aşımı belirttiğinde, <xref:System.Transactions.TransactionScope> nesne üzerinde yeni, daha kısa zaman aşımı zorlanır ve kapsam belirtilen iç içe geçen süre içinde sona ermeli veya işlem otomatik olarak iptal edilir. İç içe geçme süresi ortam hareketinden daha fazlaysa, hiçbir etkisi yoktur.  
  
## <a name="setting-the-transactionscope-isolation-level"></a>TransactionScope yalıtım düzeyini ayarlama  
 Zaman aşma değerine ek <xref:System.Transactions.TransactionScope> olarak yalıtım düzeyi <xref:System.Transactions.TransactionOptions> belirtmek için aşırı yüklü yapıyı kabul eden aşırı yüklü yapıcılardan bazıları. Varsayılan olarak, hareket yalıtım düzeyi <xref:System.Transactions.IsolationLevel.Serializable>olarak ayarlanmış yürütülür. Başka bir yalıtım düzeyi seçme <xref:System.Transactions.IsolationLevel.Serializable> yaygın olarak okuma yoğun sistemleri için kullanılır. Bu, işlem işleme teorisive işlemin kendisinin anlambiliminin, eşzamanlılık sorunlarının ve sistem tutarlılığının sonuçlarının sağlam bir şekilde anlaşılmasını gerektirir.  
  
 Buna ek olarak, tüm kaynak yöneticileri tüm yalıtım düzeylerini desteklemez ve yapılandırılandan daha yüksek bir düzeyde işlemde yer almayı seçebilirler.  
  
 Aynı bilgilere <xref:System.Transactions.IsolationLevel.Serializable> erişen diğer işlemlerden kaynaklanan tutarsızlığa karşı her yalıtım düzeyi de açıktır. Farklı yalıtım düzeyleri arasındaki farkı biçiminde okunur ve yazma kilitler kullanılır. Kilit yalnızca işlem kaynak yöneticisindeki verilere eriştığında veya hareket işlenene veya iptal edilene kadar tutulabilir. Eski verimlilik, tutarlılık ikincisi için iyidir. Kilit iki tür ve işlemleri (okuma/yazma) iki tür dört temel yalıtım düzeyi verin. Daha fazla bilgi edinmek için bkz. <xref:System.Transactions.IsolationLevel>.  
  
 İç içe <xref:System.Transactions.TransactionScope> geçen nesneler kullanılırken, ortam hareketine katılmak istiyorlarsa, iç içe geçen tüm kapsamların tam olarak aynı yalıtım düzeyini kullanacak şekilde yapılandırılması gerekir. İç içe <xref:System.Transactions.TransactionScope> bir nesne ortam işlemine katılmaya çalışırsa, ancak farklı bir <xref:System.ArgumentException> yalıtım düzeyi belirtirse, bir atılır.  
  
## <a name="interop-with-com"></a>COM + ile birlikte çalışma  
 Yeni <xref:System.Transactions.TransactionScope> bir örnek oluşturduğunuzda, <xref:System.Transactions.EnterpriseServicesInteropOption> com+ ile nasıl etkileşimde kullanılacağını belirtmek için yapı oluşturuculardan birinde numaralandırmayı kullanabilirsiniz. Bu konuda daha fazla bilgi için, [Kurumsal Hizmetler ve COM+ İşlemleriyle Birlikte Çalışabilirlik'e](interoperability-with-enterprise-services-and-com-transactions.md)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Transactions.Transaction.Clone%2A>
- <xref:System.Transactions.TransactionScope>
