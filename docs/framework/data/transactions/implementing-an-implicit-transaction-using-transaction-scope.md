---
title: İşlem Kapsamı Kullanarak Örtük İşlem Uygulama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49d1706a-1e0c-4c85-9704-75c908372eb9
ms.openlocfilehash: e3af361f4268e9a83efe4d28547dc95fc242633e
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040209"
---
# <a name="implementing-an-implicit-transaction-using-transaction-scope"></a>İşlem Kapsamı Kullanarak Örtük İşlem Uygulama
<xref:System.Transactions.TransactionScope> sınıfı, bir kod bloğunu işlem kendisiyle etkileşime girmeden bir işleme katıldıkları şekilde işaretlemek için basit bir yol sağlar. İşlem kapsamı, ortam işlemini otomatik olarak seçebilir ve yönetebilir. Kullanım kolaylığı ve verimlilik nedeniyle, bir işlem uygulaması geliştirirken <xref:System.Transactions.TransactionScope> sınıfını kullanmanız önerilir.  
  
 Ayrıca, işlemle birlikte listeleme kaynaklarına gerek kalmaz. Herhangi bir <xref:System.Transactions> Resource Manager (SQL Server 2005 gibi), kapsam tarafından oluşturulan bir ortam işleminin varlığını algılayabilir ve otomatik olarak listeleme yapabilir.  
  
## <a name="creating-a-transaction-scope"></a>İşlem kapsamı oluşturma  
 Aşağıdaki örnek, bir basit kullanımını gösterir <xref:System.Transactions.TransactionScope> sınıfı.  
  
 [!code-csharp[TransactionScope#1](../../../../samples/snippets/csharp/VS_Snippets_Remoting/TransactionScope/cs/ScopeWithSQL.cs#1)]
 [!code-vb[TransactionScope#1](../../../../samples/snippets/visualbasic/VS_Snippets_Remoting/TransactionScope/vb/ScopeWithSQL.vb#1)]  
  
 Yeni bir <xref:System.Transactions.TransactionScope> nesnesi oluşturduktan sonra işlem kapsamı başlatılır.  Kod örneğinde gösterildiği gibi, `using` bir ifadesiyle kapsam oluşturmanız önerilir. `using` deyimin her ikisi de Visual Basic C# ve içinde kullanılabilir ve kapsamın doğru bir şekilde atıldığından emin olmak için bir`try`...`finally`bloğu gibi çalışıyor.  
  
 <xref:System.Transactions.TransactionScope>örneklediğinizde, işlem Yöneticisi hangi hareketin katılacağı belirler. Belirlendikten sonra, kapsam her zaman bu işleme katılır. Bu karar, iki etkene dayalıdır: bir ortam işleminin mevcut olup olmadığı ve oluşturucuda `TransactionScopeOption` parametresinin değeri. Çevresel işlem, kodunuzun çalıştırıldığı işlemdir. <xref:System.Transactions.Transaction> sınıfının statik <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType> özelliğini çağırarak çevresel işleme bir başvuru elde edebilirsiniz. Bu parametrenin nasıl kullanıldığı hakkında daha fazla bilgi için, bu konunun [TransactionScopeOption kullanılarak işlem akışını yönetme](#ManageTxFlow) bölümüne bakın.  
  
## <a name="completing-a-transaction-scope"></a>İşlem kapsamını tamamlama  
 Uygulamanız bir işlemde gerçekleştirmek istediği tüm işleri tamamladığında, işlem yöneticisini işleme için kabul edilebilir olduğunu bildirmek için <xref:System.Transactions.TransactionScope.Complete%2A?displayProperty=nameWIthType> yöntemini yalnızca bir kez çağırmanız gerekir. Çağrı yerleştirmek için çok iyi bir uygulamadır <xref:System.Transactions.TransactionScope.Complete%2A> son ifade olarak `using` blok.  
  
 İşlem yöneticisi bunu bir sistem hatası olarak yorumladığı ya da işlemin kapsamında oluşturulan bir özel durumla eşdeğer olduğundan, bu yöntemi çağıramaması işlemi iptal eder. Ancak, bu yöntemin çağrılması, işlem WIL 'nin uygulanabileceğini garanti etmez. Yalnızca durumlarınızın işlem yöneticisini bilgilendiren bir yoldur. <xref:System.Transactions.TransactionScope.Complete%2A> yöntemini çağırdıktan sonra, <xref:System.Transactions.Transaction.Current%2A> özelliğini kullanarak çevresel işleme erişemeyecektir ve bunu yapmaya çalıştığınızda bir özel durum oluşur.  
  
 <xref:System.Transactions.TransactionScope> nesnesi başlangıçta ilk kez oluşturulduysa, işlemi işlem yöneticisi tarafından yürütmek için gerçek iş, `using` bloğundaki kodun son satırından sonra oluşur. İşlem oluşturamadığında, <xref:System.Transactions.CommittableTransaction.Commit%2A> <xref:System.Transactions.CommittableTransaction> nesnesinin sahibi tarafından her çağrıldığında işleme oluşur. Bu noktada, işlem yöneticisi kaynak yöneticilerini çağırır ve <xref:System.Transactions.TransactionScope.Complete%2A> yönteminin <xref:System.Transactions.TransactionScope> nesnesinde çağrılıp çağrılmayacağı temel alınarak bunları COMMIT veya Rollback olarak bilgilendirir.  
  
 `using` Bildirimi sağlar <xref:System.Transactions.TransactionScope.Dispose%2A> yöntemi <xref:System.Transactions.TransactionScope> nesne bile özel bir durum oluştuğunda çağrılır. <xref:System.Transactions.TransactionScope.Dispose%2A> yöntemi işlem kapsamının sonunu işaretler. Bu yöntemi çağırdıktan sonra oluşan özel durumlar işlemi etkilemeyebilir. Bu yöntem aynı zamanda çevresel işlemi önceki durumuna geri yükler.  
  
 Kapsam işlemi oluşturduğunda <xref:System.Transactions.TransactionAbortedException> oluşturulur ve işlem iptal edilir. İşlem Yöneticisi bir Işleme kararına ulaşamadıysanız bir <xref:System.Transactions.TransactionInDoubtException> oluşturulur. İşlem yürütüldüğünden hiçbir özel durum oluşturulmaz.  
  
## <a name="rolling-back-a-transaction"></a>Bir işlem geri alınıyor  
 Bir işlemi geri almak istiyorsanız, işlem kapsamı içinde <xref:System.Transactions.TransactionScope.Complete%2A> yöntemini çağırmamalıdır. Örneğin, kapsam içinde bir özel durum. İçindeki katıldığı işlem geri alınacaktır.  
  
## <a name="ManageTxFlow"></a>TransactionScopeOption kullanarak işlem akışını yönetme  
 İşlem kapsamı, aşağıdaki örnekteki `RootMethod` yönteminde olduğu gibi, kendi kapsamını kullanan bir yöntem içinde <xref:System.Transactions.TransactionScope> kullanan bir yöntemi çağırarak iç içe olabilir.  
  
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
  
 En üst işlem kapsamı kök kapsamı olarak adlandırılır.  
  
 <xref:System.Transactions.TransactionScope> sınıfı, kapsamın işlem davranışını tanımlayan <xref:System.Transactions.TransactionScopeOption>türünün bir numaralandırmasını kabul eden birkaç aşırı yüklü Oluşturucu sağlar.  
  
 Bir <xref:System.Transactions.TransactionScope> nesnenin üç seçenek vardır:  
  
- Ortam işlemine katılır veya bir tane yoksa yeni bir tane oluşturun.  
  
- Yeni bir kök kapsamı olun, yani yeni bir işlem başlatın ve bu işlemin kendi kapsamı içinde yeni çevresel işlem olmasını sağlayabilirsiniz.  
  
- Bir işlemde bir işlem olmaz. Sonuç olarak ortam işlemi yoktur.  
  
 Kapsam <xref:System.Transactions.TransactionScopeOption.Required>ile örneklenmiştir ve bir ortam işlemi mevcutsa, kapsam bu işlemi birleştirir. Diğer taraftan, ortam işlemi yoksa, kapsam yeni bir işlem oluşturur ve kök kapsamı olur. Varsayılan değer budur. <xref:System.Transactions.TransactionScopeOption.Required> kullanıldığında, kapsamın içindeki kodun, kök olup olmadığı veya yalnızca ortam hareketine katılması gibi farklı davranması gerekmez. Her iki durumda da aynı şekilde çalışması.  
  
 Kapsamı ile örneği varsa <xref:System.Transactions.TransactionScopeOption.RequiresNew>, her zaman bir kök kapsam olur. Yeni bir işlem başlatır ve işlem, kapsam içindeki yeni çevresel işlem haline gelir.  
  
 Kapsam <xref:System.Transactions.TransactionScopeOption.Suppress>ile örneklendiğinden, bir ortam işleminin mevcut olup olmamasından bağımsız olarak hiçbir zaman bir işlemde yer almıyor. Bu değerle örneklenen bir kapsam, her zaman çevresel işlem olarak `null` sahiptir.  
  
 Yukarıdaki seçenekleri aşağıdaki tabloda özetlenmiştir.  
  
|TransactionScopeOption|Çevresel Işlem|Kapsam bölümü alır|  
|----------------------------|-------------------------|-----------------------------|  
|Gerekli|Hayır|Yeni Işlem (kök olacaktır)|  
|Yeni gerektirir|Hayır|Yeni Işlem (kök olacaktır)|  
|Önle|Hayır|Işlem yok|  
|Gerekli|Evet|Çevresel Işlem|  
|Yeni gerektirir|Evet|Yeni Işlem (kök olacaktır)|  
|Önle|Evet|Işlem yok|  
  
 Bir <xref:System.Transactions.TransactionScope> nesnesi var olan bir ortam işlemine katıldığında kapsam nesnesini elden atma işlemi, kapsam işlemi iptal etmediği takdirde işlemi sonlandırmayabilir. Ortam işlemi bir kök kapsam tarafından oluşturulduysa, yalnızca kök kapsamı bırakıldığında, işlem üzerinde <xref:System.Transactions.CommittableTransaction.Commit%2A> çağırılır. İşlem el ile oluşturulduysa, işlem iptal edildiğinde ya da Oluşturucusu tarafından işlendiği zaman sona erer.  
  
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
  
 Örnek, <xref:System.Transactions.TransactionScopeOption.Required>ile yeni bir kapsam (`scope1`) oluşturan herhangi bir ortam işlemi olmadan bir kod bloğunu gösterir. `scope1` kapsam, yeni bir işlem (Işlem A) oluşturduğu ve Işlem bir ortam işlemi yaptığı için bir kök kapsamdır. `Scope1`Daha sonra her farklı bir ile üç daha fazla nesne oluşturur <xref:System.Transactions.TransactionScopeOption> değeri. Örneğin, `scope2` <xref:System.Transactions.TransactionScopeOption.Required>ile oluşturulur ve ortam bir işlem olduğundan, `scope1`tarafından oluşturulan ilk işlemi birleştirir. `scope3` yeni bir işlemin kök kapsamı olduğunu ve `scope4` bir ortam işlemi olmadığını unutmayın.  
  
 Değerini varsayılan ve en sık kullanılan olsa da <xref:System.Transactions.TransactionScopeOption> olan <xref:System.Transactions.TransactionScopeOption.Required>, her diğer değerlerinin benzersiz amacı vardır.  

### <a name="non-transactional-code-inside-a-transaction-scope"></a>İşlem kapsamı içinde işlem olmayan kod

 <xref:System.Transactions.TransactionScopeOption.Suppress>, kod bölümü tarafından gerçekleştirilen işlemleri korumak istediğinizde ve işlemler başarısız olursa çevresel işlemi durdurmak istemediğinizde yararlıdır. Örneğin, günlüğe kaydetme veya denetim işlemleri gerçekleştirmek istediğinizde ya da çevresel işleminizi yürütmelerden veya iptal etmeksizin bağımsız olarak abonelere yayımlamak istediğinizde. Bu değer, aşağıdaki örnekte gösterildiği gibi işlem kapsamı içinde işlem olmayan bir kod bölümüne sahip etmenize olanak tanır.  
  
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
 İç içe kapsam, kök kapsamın çevresel hareketini birleştirebilse de, iç içe kapsamdaki <xref:System.Transactions.TransactionScope.Complete%2A> çağırmak kök kapsamda hiçbir etkisi olmaz. Yalnızca kök kapsamdaki en son iç içe kapsama kadar olan tüm kapsamlar işlemi yürütmek için oy alırsanız işlem kaydedilir. İç içe bir kapsamda <xref:System.Transactions.TransactionScope.Complete%2A> çağrılmayan kök kapsamı, ortam işlemi hemen iptal edilecek şekilde etkiler.  
  
## <a name="setting-the-transactionscope-timeout"></a>TransactionScope zaman aşımını ayarlama  
 <xref:System.Transactions.TransactionScope> aşırı yüklenmiş oluşturucularından bazıları, işlemin zaman aşımını denetlemek için kullanılan <xref:System.TimeSpan>türünde bir değer kabul eder. Sıfır olarak ayarlanmış bir zaman aşımı sonsuz bir zaman aşımı anlamına gelir. Sonsuz zaman aşımı genellikle hata ayıklama için yararlıdır, kodunuzda adım adım ilerleyerek iş mantığınızdaki bir sorunu yalıtmak istediğinizde ve sorunu bulmaya çalışırken hata ayıklama işlemini zaman aşımına uğratın. Tüm diğer durumlarda sonsuz zaman aşımı değerini kullanırken son derece dikkatli olun, çünkü işlem kilitlenmeleri için korumaları geçersiz kılar.  
  
 Genellikle ayarlanabilir <xref:System.Transactions.TransactionScope> zaman aşımına uğramak üzere iki durumda da varsayılan dışındaki değerler. Birincisi geliştirme sırasında, uygulamanızın durdurulan işlemleri işleme biçimini test etmek istediğinizde olur. Zaman aşımını küçük bir değere (örneğin bir milisaniyelik) ayarlayarak, işlem başarısız olur ve bu nedenle hata işleme kodunuzu gözlemleyebilirsiniz. Kapsam içinde kaynak talebi, söz konusu kilitlenmeleri kaynaklanan düşünüyorsanız, varsayılan zaman aşımı değerinden bir değere ayarlamanız ikinci durumdur. Bu durumda, işlemi en kısa sürede iptal etmek ve varsayılan zaman aşımı süresinin dolmasını beklemek istemezsiniz.  
  
 Bir kapsam bir ortam işlemini birleşdiğinde, ancak ortam işleminin ayarlandığı değerden daha küçük bir zaman aşımı belirttiğinde, yeni ve daha kısa zaman aşımı <xref:System.Transactions.TransactionScope> nesnesinde zorlanır ve kapsam belirtilen iç içe geçen süre içinde bitmelidir veya işlem otomatik olarak iptal edildi. İç içe geçmiş kapsamın zaman aşımı çevresel işlemden daha büyükse, hiçbir etkisi olmaz.  
  
## <a name="setting-the-transactionscope-isolation-level"></a>TransactionScope yalıtım düzeyini ayarlama  
 <xref:System.Transactions.TransactionScope> aşırı yüklenmiş oluşturucularından bazıları, bir zaman aşımı değerine ek olarak bir yalıtım düzeyi belirtmek için <xref:System.Transactions.TransactionOptions> türünde bir yapıyı kabul eder. Varsayılan olarak, işlem yalıtım düzeyiyle yürütülür ve <xref:System.Transactions.IsolationLevel.Serializable>olarak ayarlanır. Başka bir yalıtım düzeyi seçme <xref:System.Transactions.IsolationLevel.Serializable> yaygın olarak okuma yoğun sistemleri için kullanılır. Bunun için işlem işleme teorisi ve işlem semantiğinin, ilgili eşzamanlılık sorunlarının ve sistem tutarlılığı sonuçlarının bir katı şekilde anlaşılması gerekir.  
  
 Ayrıca, tüm kaynak yöneticileri tüm yalıtım düzeylerini desteklemez ve bu işlem, bir şekilde, yapılandırılmış olandan daha yüksek bir düzeyde bir parça almak isteyebilir.  
  
 <xref:System.Transactions.IsolationLevel.Serializable> yanı sıra her yalıtım düzeyi, aynı bilgilere erişen diğer işlemlerden kaynaklanan tutarsızlığa açıktır. Farklı yalıtım düzeyleri arasındaki farkı biçiminde okunur ve yazma kilitler kullanılır. Bir kilit, yalnızca işlem Resource Manager 'daki verilere eriştiğinde tutulabilir veya işlem tamamlanana ya da durduruluncaya kadar tutulabilirler. Eski verimlilik, tutarlılık ikincisi için iyidir. Kilit iki tür ve işlemleri (okuma/yazma) iki tür dört temel yalıtım düzeyi verin. Daha fazla bilgi edinmek için bkz. <xref:System.Transactions.IsolationLevel>.  
  
 İç içe <xref:System.Transactions.TransactionScope> nesneleri kullanılırken, tüm iç içe kapsamlar çevresel işleme katmak istiyorsanız tam olarak aynı yalıtım düzeyini kullanacak şekilde yapılandırılmalıdır. İç içe bir <xref:System.Transactions.TransactionScope> nesnesi, farklı bir yalıtım düzeyi belirttiğinde, ancak bir <xref:System.ArgumentException> oluşturulur.  
  
## <a name="interop-with-com"></a>COM + ile birlikte çalışma  
 Yeni bir <xref:System.Transactions.TransactionScope> örneği oluşturduğunuzda, COM+ ile nasıl etkileşim kuracağınızı belirtmek için oluşturuculardan birinde <xref:System.Transactions.EnterpriseServicesInteropOption> numaralandırmayı kullanabilirsiniz. Bu konuda daha fazla bilgi için bkz. [Enterprise Services ve com+ işlemleri Ile birlikte çalışabilirlik](interoperability-with-enterprise-services-and-com-transactions.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Transactions.Transaction.Clone%2A>
- <xref:System.Transactions.TransactionScope>
