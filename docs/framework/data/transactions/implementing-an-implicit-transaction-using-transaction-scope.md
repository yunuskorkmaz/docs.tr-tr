---
title: İşlem Kapsamı Kullanarak Örtük İşlem Uygulama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49d1706a-1e0c-4c85-9704-75c908372eb9
ms.openlocfilehash: 3a6dd2cc4565cd4f8716b691d564a782887be1e0
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205929"
---
# <a name="implementing-an-implicit-transaction-using-transaction-scope"></a>İşlem Kapsamı Kullanarak Örtük İşlem Uygulama
<xref:System.Transactions.TransactionScope> Sınıfı, bir kod bloğunu bir işlem içine katılımınıza, işlem kendisiyle etkileşime girmeden işaretlemek için basit bir yol sağlar. İşlem kapsamı, ortam işlemini otomatik olarak seçebilir ve yönetebilir. Kullanım kolaylığı ve verimlilik nedeniyle, bir işlem uygulaması geliştirirken <xref:System.Transactions.TransactionScope> sınıfını kullanmanız önerilir.  
  
 Ayrıca, işlemle birlikte listeleme kaynaklarına gerek kalmaz. Herhangi <xref:System.Transactions> bir kaynak yöneticisi (SQL Server 2005 gibi), kapsam tarafından oluşturulan bir ortam işleminin varlığını algılayabilir ve otomatik olarak listeleme yapabilir.  
  
## <a name="creating-a-transaction-scope"></a>İşlem kapsamı oluşturma  
 Aşağıdaki örnek, bir basit kullanımını gösterir <xref:System.Transactions.TransactionScope> sınıfı.  
  
 [!code-csharp[TransactionScope#1](../../../../samples/snippets/csharp/VS_Snippets_Remoting/TransactionScope/cs/ScopeWithSQL.cs#1)]
 [!code-vb[TransactionScope#1](../../../../samples/snippets/visualbasic/VS_Snippets_Remoting/TransactionScope/vb/ScopeWithSQL.vb#1)]  
  
 Yeni <xref:System.Transactions.TransactionScope> bir nesne oluşturduktan sonra işlem kapsamı başlatılır.  Kod örneğinde gösterildiği gibi, **using** ifadesiyle kapsam oluşturmanız önerilir. **Using** deyimleri, hem içinde C# hem de Visual Basic kullanılabilir ve bir TRY gibi çalışır.. **. son olarak** , kapsamın doğru bir şekilde atıldığından emin olmak için bloğu.  
  
 Örneğini <xref:System.Transactions.TransactionScope>oluşturduğunuzda, işlem Yöneticisi hangi hareketin katılacağı belirler. Belirlendikten sonra, kapsam her zaman bu işleme katılır. Karar iki etkene dayalıdır: bir ortam işleminin mevcut olup olmadığı ve oluşturucudaki **TransactionScopeOption** parametresinin değeri. Çevresel işlem, kodunuzun çalıştırıldığı işlemdir. <xref:System.Transactions.Transaction> Sınıfının statik <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType> özelliğini çağırarak çevresel işleme bir başvuru elde edebilirsiniz. Bu parametrenin nasıl kullanıldığı hakkında daha fazla bilgi için, bu konunun [TransactionScopeOption kullanılarak işlem akışını yönetme](#ManageTxFlow) bölümüne bakın.  
  
## <a name="completing-a-transaction-scope"></a>İşlem kapsamını tamamlama  
 Uygulamanız bir işlemde gerçekleştirmek istediği tüm işleri tamamladığında, işlem yöneticisini işlem yürütmek için kabul edilebilir olduğunu bildirmek üzere <xref:System.Transactions.TransactionScope.Complete%2A?displayProperty=nameWIthType> yöntemi yalnızca bir kez çağırmanız gerekir. Çağrısını <xref:System.Transactions.TransactionScope.Complete%2A> , **using** bloğunda son ifadeye koymak çok iyi bir uygulamadır.  
  
 İşlem yöneticisi bunu bir sistem hatası olarak yorumladığı ya da işlemin kapsamında oluşturulan bir özel durumla eşdeğer olduğundan, bu yöntemi çağıramaması işlemi iptal eder. Ancak, bu yöntemin çağrılması, işlem WIL 'nin uygulanabileceğini garanti etmez. Yalnızca durumlarınızın işlem yöneticisini bilgilendiren bir yoldur. <xref:System.Transactions.TransactionScope.Complete%2A> Yöntemini çağırdıktan sonra, <xref:System.Transactions.Transaction.Current%2A> özelliği kullanarak çevresel işleme erişemeyecektir ve bunu yapmaya çalıştığınızda bir özel durum oluşturulması neden olur.  
  
 Nesneyi başlangıçta oluşturmadıysa, işlem yöneticisi tarafından işlem yürütmek için gerçek iş, using bloğundaki kodun son satırından sonra oluşur. <xref:System.Transactions.TransactionScope> İşlem oluşturamadığında, işleme <xref:System.Transactions.CommittableTransaction.Commit%2A> <xref:System.Transactions.CommittableTransaction> nesnenin sahibi tarafından her çağrıldığında gerçekleşir. Bu noktada, işlem yöneticisi kaynak yöneticilerini çağırır ve <xref:System.Transactions.TransactionScope.Complete%2A> yöntemin <xref:System.Transactions.TransactionScope> nesne üzerinde çağrılıp çağrılmayacağı temelinde bunları COMMIT veya Rollback olarak bilgilendirir.  
  
 **Using** deyimleri, bir özel durum <xref:System.Transactions.TransactionScope.Dispose%2A> meydana gelirse bile <xref:System.Transactions.TransactionScope> nesne yönteminin çağrılması sağlar. <xref:System.Transactions.TransactionScope.Dispose%2A> Yöntemi, işlem kapsamının sonunu işaretler. Bu yöntemi çağırdıktan sonra oluşan özel durumlar işlemi etkilemeyebilir. Bu yöntem aynı zamanda çevresel işlemi önceki durumuna geri yükler.  
  
 <xref:System.Transactions.TransactionAbortedException> , Kapsam işlemi oluşturduğunda oluşturulur ve işlem iptal edilir. İşlem Yöneticisi bir işleme kararına ulaşamadıysanız ,oluşturulur.<xref:System.Transactions.TransactionInDoubtException> İşlem yürütüldüğünden hiçbir özel durum oluşturulmaz.  
  
## <a name="rolling-back-a-transaction"></a>Bir işlem geri alınıyor  
 Bir işlemi geri almak istiyorsanız, <xref:System.Transactions.TransactionScope.Complete%2A> yöntemi işlem kapsamı içinde çağırmamalıdır. Örneğin, kapsam içinde bir özel durum. İçindeki katıldığı işlem geri alınacaktır.  
  
## <a name="ManageTxFlow"></a>TransactionScopeOption kullanarak işlem akışını yönetme  
 İşlem kapsamı, `RootMethod` yöntemi aşağıdaki örnekte olduğu gibi, kendi kapsamını kullanan <xref:System.Transactions.TransactionScope> bir yöntemin içinden öğesini kullanan bir yöntemi çağırarak iç içe olabilir.  
  
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
  
 Sınıfı, kapsamın işlem davranışını tanımlayan, türün <xref:System.Transactions.TransactionScopeOption>bir listesini kabul eden birkaç aşırı yüklenmiş Oluşturucu sağlar. <xref:System.Transactions.TransactionScope>  
  
 Bir <xref:System.Transactions.TransactionScope> nesnenin üç seçenek vardır:  
  
- Ortam işlemine katılır veya bir tane yoksa yeni bir tane oluşturun.  
  
- Yeni bir kök kapsamı olun, yani yeni bir işlem başlatın ve bu işlemin kendi kapsamı içinde yeni çevresel işlem olmasını sağlayabilirsiniz.  
  
- Bir işlemde bir işlem olmaz. Sonuç olarak ortam işlemi yoktur.  
  
 Kapsamı ile <xref:System.Transactions.TransactionScopeOption.Required>örneği varsa ve bir ortam işlemi mevcutsa, kapsam bu işlemi birleştirir. Diğer taraftan, ortam işlemi yoksa, kapsam yeni bir işlem oluşturur ve kök kapsamı olur. Varsayılan değer budur. <xref:System.Transactions.TransactionScopeOption.Required> Kullanıldığında, kapsamın içindeki kodun kök olup olmadığı veya yalnızca ortam hareketine katılması gibi farklı davranması gerekmez. Her iki durumda da aynı şekilde çalışması.  
  
 Kapsamı ile örneği varsa <xref:System.Transactions.TransactionScopeOption.RequiresNew>, her zaman bir kök kapsam olur. Yeni bir işlem başlatır ve işlem, kapsam içindeki yeni çevresel işlem haline gelir.  
  
 Kapsamı ile <xref:System.Transactions.TransactionScopeOption.Suppress>örneği varsa, bir ortam işleminin mevcut olup olmamasına bakılmaksızın hiçbir zaman bir işlemde yer almıyor. Bu değerle örneklenmiş bir kapsam, her zaman çevresel işlemi olarak **null değeri** içermelidir.  
  
 Yukarıdaki seçenekleri aşağıdaki tabloda özetlenmiştir.  
  
|TransactionScopeOption|Çevresel Işlem|Kapsam bölümü alır|  
|----------------------------|-------------------------|-----------------------------|  
|Gerekli|Hayır|Yeni Işlem (kök olacaktır)|  
|Yeni gerektirir|Hayır|Yeni Işlem (kök olacaktır)|  
|Önle|Hayır|Işlem yok|  
|Gerekli|Evet|Çevresel Işlem|  
|Yeni gerektirir|Evet|Yeni Işlem (kök olacaktır)|  
|Önle|Evet|Işlem yok|  
  
 Bir <xref:System.Transactions.TransactionScope> nesne var olan bir ortam işlemine katıldığında kapsam nesnesini elden atma işlemi, kapsam işlemi iptal etmediği takdirde işlemi sonlandırmayabilir. Ortam işlemi bir kök kapsam tarafından oluşturulduysa, yalnızca kök kapsamı bırakıldığında, <xref:System.Transactions.CommittableTransaction.Commit%2A> işlem üzerinde çağırılır. İşlem el ile oluşturulduysa, işlem iptal edildiğinde ya da Oluşturucusu tarafından işlendiği zaman sona erer.  
  
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
  
 Örnek, ile`scope1` <xref:System.Transactions.TransactionScopeOption.Required>yeni bir kapsam () oluşturan herhangi bir ortam işlemini içermeyen bir kod bloğunu gösterir. Kapsam `scope1` , yeni bir işlem (işlem a) oluşturduğu ve işlemi çevresel işlem yapan bir kök kapsamdır. `Scope1`Daha sonra her farklı bir ile üç daha fazla nesne oluşturur <xref:System.Transactions.TransactionScopeOption> değeri. Örneğin, `scope2` ile <xref:System.Transactions.TransactionScopeOption.Required>oluşturulur ve bir ortam işlemi olduğundan, tarafından `scope1`oluşturulan ilk işlemi birleştirir. Bu `scope3` , yeni bir işlemin kök kapsamı `scope4` ve ortam işlemi olmadığını unutmayın.  
  
 Değerini varsayılan ve en sık kullanılan olsa da <xref:System.Transactions.TransactionScopeOption> olan <xref:System.Transactions.TransactionScopeOption.Required>, her diğer değerlerinin benzersiz amacı vardır.  

### <a name="non-transactional-code-inside-a-transaction-scope"></a>İşlem kapsamı içinde işlem olmayan kod

 <xref:System.Transactions.TransactionScopeOption.Suppress>kod bölümü tarafından gerçekleştirilen işlemleri korumak istediğinizde ve işlemler başarısız olursa ortam işlemini durdurmak istemediğinizde yararlıdır. Örneğin, günlüğe kaydetme veya denetim işlemleri gerçekleştirmek istediğinizde ya da çevresel işleminizi yürütmelerden veya iptal etmeksizin bağımsız olarak abonelere yayımlamak istediğinizde. Bu değer, aşağıdaki örnekte gösterildiği gibi işlem kapsamı içinde işlem olmayan bir kod bölümüne sahip etmenize olanak tanır.  
  
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
 İç içe bir kapsam kök kapsamın çevresel hareketine katılabilse de, iç içe kapsamda <xref:System.Transactions.TransactionScope.Complete%2A> çağırma, kök kapsamı üzerinde hiçbir etkisi olmaz. Yalnızca kök kapsamdaki en son iç içe kapsama kadar olan tüm kapsamlar işlemi yürütmek için oy alırsanız işlem kaydedilir. İç içe <xref:System.Transactions.TransactionScope.Complete%2A> bir kapsamda çağrılmayan ortam işlemi hemen iptal edilecek şekilde kök kapsamı etkiler.  
  
## <a name="setting-the-transactionscope-timeout"></a>TransactionScope zaman aşımını ayarlama  
 Öğesinin zaman aşımını denetlemek için kullanılan <xref:System.Transactions.TransactionScope> , türünde <xref:System.TimeSpan>bir değer kabul etmenin bazı aşırı yüklenmiş oluşturucularından bazıları. Sıfır olarak ayarlanmış bir zaman aşımı sonsuz bir zaman aşımı anlamına gelir. Sonsuz zaman aşımı genellikle hata ayıklama için yararlıdır, kodunuzda adım adım ilerleyerek iş mantığınızdaki bir sorunu yalıtmak istediğinizde ve sorunu bulmaya çalışırken hata ayıklama işlemini zaman aşımına uğratın. Tüm diğer durumlarda sonsuz zaman aşımı değerini kullanırken son derece dikkatli olun, çünkü işlem kilitlenmeleri için korumaları geçersiz kılar.  
  
 Genellikle ayarlanabilir <xref:System.Transactions.TransactionScope> zaman aşımına uğramak üzere iki durumda da varsayılan dışındaki değerler. Birincisi geliştirme sırasında, uygulamanızın durdurulan işlemleri işleme biçimini test etmek istediğinizde olur. Zaman aşımını küçük bir değere (örneğin bir milisaniyelik) ayarlayarak, işlem başarısız olur ve bu nedenle hata işleme kodunuzu gözlemleyebilirsiniz. Kapsam içinde kaynak talebi, söz konusu kilitlenmeleri kaynaklanan düşünüyorsanız, varsayılan zaman aşımı değerinden bir değere ayarlamanız ikinci durumdur. Bu durumda, işlemi en kısa sürede iptal etmek ve varsayılan zaman aşımı süresinin dolmasını beklemek istemezsiniz.  
  
 Bir kapsam bir ortam işlemini birleşdiğinde, ancak ortam işleminin ayarlandığı değerden daha küçük bir zaman aşımı belirttiğinde, yeni, daha kısa zaman aşımı <xref:System.Transactions.TransactionScope> nesne üzerinde zorlanır ve kapsam belirtilen iç içe geçen süre içinde bitmelidir ya da işlem şu şekilde olmalıdır otomatik olarak iptal edildi. İç içe geçmiş kapsamın zaman aşımı çevresel işlemden daha büyükse, hiçbir etkisi olmaz.  
  
## <a name="setting-the-transactionscope-isolation-level"></a>TransactionScope yalıtım düzeyini ayarlama  
 Bir zaman aşımı değerine ek olarak <xref:System.Transactions.TransactionScope> bir yalıtım düzeyi belirtmek için <xref:System.Transactions.TransactionOptions> türünde bir yapıyı kabul etmenin bazı aşırı yüklenmiş oluşturucularından bazıları. Varsayılan olarak, işlem yalıtım düzeyi olarak ayarlanmış şekilde <xref:System.Transactions.IsolationLevel.Serializable>yürütülür. Başka bir yalıtım düzeyi seçme <xref:System.Transactions.IsolationLevel.Serializable> yaygın olarak okuma yoğun sistemleri için kullanılır. Bunun için işlem işleme teorisi ve işlem semantiğinin, ilgili eşzamanlılık sorunlarının ve sistem tutarlılığı sonuçlarının bir katı şekilde anlaşılması gerekir.  
  
 Ayrıca, tüm kaynak yöneticileri tüm yalıtım düzeylerini desteklemez ve bu işlem, bir şekilde, yapılandırılmış olandan daha yüksek bir düzeyde bir parça almak isteyebilir.  
  
 Her yalıtım düzeyi <xref:System.Transactions.IsolationLevel.Serializable> , aynı bilgilere erişen diğer işlemlerden kaynaklanan tutarsızlığa açıktır. Farklı yalıtım düzeyleri arasındaki farkı biçiminde okunur ve yazma kilitler kullanılır. Bir kilit, yalnızca işlem Resource Manager 'daki verilere eriştiğinde tutulabilir veya işlem tamamlanana ya da durduruluncaya kadar tutulabilirler. Eski verimlilik, tutarlılık ikincisi için iyidir. Kilit iki tür ve işlemleri (okuma/yazma) iki tür dört temel yalıtım düzeyi verin. Daha fazla bilgi edinmek için bkz. <xref:System.Transactions.IsolationLevel>.  
  
 İç içe <xref:System.Transactions.TransactionScope> nesneler kullanılırken, tüm iç içe kapsamlar çevresel işleme katmak istediklerinde tam olarak aynı yalıtım düzeyini kullanacak şekilde yapılandırılmalıdır. Yuvalanmış <xref:System.Transactions.TransactionScope> bir nesne, ortam işlemine katılmayı denediğinde farklı bir yalıtım düzeyi belirtir, bir <xref:System.ArgumentException> oluşturulur.  
  
## <a name="interop-with-com"></a>COM + ile birlikte çalışma  
 Yeni <xref:System.Transactions.TransactionScope> bir örnek oluşturduğunuzda, com+ ile nasıl etkileşim kuracağınızı <xref:System.Transactions.EnterpriseServicesInteropOption> belirtmek için oluşturuculardan birindeki sabit listesini kullanabilirsiniz. Bu konuda daha fazla bilgi için bkz. [Enterprise Services ve com+ işlemleri Ile birlikte çalışabilirlik](interoperability-with-enterprise-services-and-com-transactions.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Transactions.Transaction.Clone%2A>
- <xref:System.Transactions.TransactionScope>
