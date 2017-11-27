---
title: "Örtük bir işlem kapsamı kullanarak işlem uygulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 49d1706a-1e0c-4c85-9704-75c908372eb9
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d33e055e9d73e786d822df2659bc490bc8646b9a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="implementing-an-implicit-transaction-using-transaction-scope"></a>Örtük bir işlem kapsamı kullanarak işlem uygulama
<xref:System.Transactions.TransactionScope> Sınıfı bir işlem ile etkileşim kurmak gerek kalmadan bir işlem içinde katılan olarak kod bloğu işaretlemek için basit bir yol sağlar. Bir işlem kapsamı seçin ve ortam işlem otomatik olarak yönetir. Kullanım kolaylığı ve verimlilik nedeniyle, kullanmanız önerilir <xref:System.Transactions.TransactionScope> hareket uygulaması geliştirilirken sınıfı.  
  
 Ayrıca, işlem açıkça kaynaklarla listeleme gerekmez. Tüm <xref:System.Transactions> Kaynak Yöneticisi (örneğin, SQL Server 2005) kapsamı tarafından oluşturulan bir ortam hareket varlığını algılayabilir ve otomatik olarak kaydolunamadı.  
  
## <a name="creating-a-transaction-scope"></a>Bir işlem kapsamı oluşturma  
 Aşağıdaki örnek, bir basit kullanımını gösterir <xref:System.Transactions.TransactionScope> sınıfı.  
  
 [!code-csharp[TransactionScope#1](../../../../samples/snippets/csharp/VS_Snippets_Remoting/TransactionScope/cs/ScopeWithSQL.cs#1)]
 [!code-vb[TransactionScope#1](../../../../samples/snippets/visualbasic/VS_Snippets_Remoting/TransactionScope/vb/ScopeWithSQL.vb#1)]  
  
 Yeni bir oluşturduktan sonra işlem kapsamı başlatıldığında <xref:System.Transactions.TransactionScope> nesnesi.  Kod örneğinde gösterildiği şekilde kapsamlarla oluşturmanız önerilir bir **kullanarak** deyimi. **Kullanarak** deyimi kullanılabilir C# ve Visual Basic ve gibi çalışır bir **try... finally** blok kapsamı düzgün bir şekilde elden emin olun.  
  
 Ne zaman örneği <xref:System.Transactions.TransactionScope>, işlem yöneticisi katılmayı hangi işlemin belirler. Belirlenen sonra kapsamı bu işlem içinde her zaman katılır. Karar iki etmenlere dayanır: ortam bir işlemin bulunup bulunmadığını ve değerini **TransactionScopeOption** Oluşturucusu parametresi. Ortam işlem içinde kodunuzu yürüten bir işlemdir. Statik çağırarak ortam işlem başvuru elde edebileceğiniz <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType> özelliği <xref:System.Transactions.Transaction> sınıfı. Bu parametre nasıl kullanıldığı hakkında daha fazla bilgi için bkz: [TransactionScopeOption kullanarak işlem akışını yönetme](#ManageTxFlow) bölümüne.  
  
## <a name="completing-a-transaction-scope"></a>Bir işlem kapsamı Tamamlanıyor  
 Uygulamanız tüm iş tamamlandığında işlemde gerçekleştirmek istediği, çağırmalısınız <xref:System.Transactions.TransactionScope.Complete%2A?displayProperty=nameWIthType> işlem yöneticisi hareketi kabul edilebilir olduğunu bildirmek için yalnızca bir kez yöntemi. Çağrı put çok iyi bir uygulamadır <xref:System.Transactions.TransactionScope.Complete%2A> son ifade olarak **kullanarak** bloğu.  
  
 İşlem Yöneticisi bunu bir sistem hatası veya işlem kapsamı içinde oluşturulan bir özel eşdeğer olarak yorumlar için bu yöntemi çağırmak başarısız olan işlem durdurur. Ancak, bu yöntemi çağırmadan, işlem garanti etmez wil kaydedilmiş. Bu işlem yöneticisi, durumunu bildiren, yalnızca bir yoludur. Çağırdıktan sonra <xref:System.Transactions.TransactionScope.Complete%2A> yöntemini kullanarak ortam işlem artık erişemez <xref:System.Transactions.Transaction.Current%2A> özelliği ve denenirse oluşturulan bir özel durum oluşur.  
  
 Varsa <xref:System.Transactions.TransactionScope> işlem başlangıçta, oluşturulan kodda son satırından sonra işlem işlem yöneticisi tarafından yürütülen gerçek iş oluşur nesne **kullanarak** bloğu. İşlem oluşturmadıysanız, yürütme zaman oluşur <xref:System.Transactions.CommittableTransaction.Commit%2A> sahibi tarafından adlı <xref:System.Transactions.CommittableTransaction> nesnesi. Bu noktada işlem yöneticisi kaynak yöneticileri çağırır ve yürütme veya geri alma olup olmadığına göre göre bunları size bildirir <xref:System.Transactions.TransactionScope.Complete%2A> yöntemi çağrıldı <xref:System.Transactions.TransactionScope> nesnesi.  
  
 **Kullanarak** deyimi sağlar <xref:System.Transactions.TransactionScope.Dispose%2A> yöntemi <xref:System.Transactions.TransactionScope> nesnesi, bir özel durum oluştuğunda dahi çağrılır. <xref:System.Transactions.TransactionScope.Dispose%2A> Yöntemi işlem kapsamı sonunu işaretler. Bu yöntemin çağrılması işlem etkilemeyebilir sonra oluşan özel durumlar. Bu yöntem aynı zamanda ortam işlem için önceki durumuna geri yükler.  
  
 A <xref:System.Transactions.TransactionAbortedException> işlem kapsam oluşturur ve işlem durduruldu durumunda oluşturulur. A <xref:System.Transactions.TransactionInDoubtException> işlem yöneticisi bir yürütme karar erişemezse atılır. İşlem tamamlanırsa hiçbir özel durum oluşur.  
  
## <a name="rolling-back-a-transaction"></a>Bir işlemi geri alınıyor  
 Bir işlemi geri almak istiyorsanız, değil çağırmalısınız <xref:System.Transactions.TransactionScope.Complete%2A> işlem kapsamı içinde yöntemi. Örneğin, kapsam içinde bir özel durum. İçinde yer aldığı işlem geri alınacak.  
  
##  <a name="ManageTxFlow"></a>İşlem akışını TransactionScopeOption kullanarak yönetme  
 İşlem kapsamı kullanan bir yöntem çağırarak iç içe geçirilemez bir <xref:System.Transactions.TransactionScope> kendi kapsamı kullanan bir yöntem içinde olarak arasındadır talebiyle `RootMethod` aşağıdaki örnekte, yöntemi  
  
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
  
 En üstteki işlem kapsamı kök kapsamı olarak adlandırılır.  
  
 <xref:System.Transactions.TransactionScope> SAX bir numaralandırma türü kabul eden birden fazla aşırı yüklenmiş oluşturucular <xref:System.Transactions.TransactionScopeOption>, kapsam işlem davranışını tanımlar.  
  
 Bir <xref:System.Transactions.TransactionScope> nesnenin üç seçenek vardır:  
  
-   Ortam işlem katılma veya bir mevcut değilse yeni bir tane oluşturun.  
  
-   Yeni bir kökü kapsamı, diğer bir deyişle, yeni bir işlem başlatmak ve bu işlem yeni ortam işlem kendi kapsamı içinde olması olmalıdır.  
  
-   Bir işlem içinde hiç katılmak değil. Sonuç olarak ortam işlem yok.  
  
 Kapsam ile örneği varsa <xref:System.Transactions.TransactionScopeOption.Required>ve bir ortam işlem mevcut ise, bu işlem kapsamı birleştirir. Diğer taraftan, varsa, hiç ortam işlem, ardından kapsamı yeni bir işlem oluşturur ve kök kapsam haline gelir. Varsayılan değer budur. Zaman <xref:System.Transactions.TransactionScopeOption.Required> olan kullanıldığında, kapsam içinde kod kök olup farklı davranır gerekmez veya yalnızca ortam işlem birleştirme. Her iki durumda da aynı şekilde çalışması.  
  
 Kapsamı ile örneği varsa <xref:System.Transactions.TransactionScopeOption.RequiresNew>, her zaman bir kök kapsam olur. Yeni bir işlem başlatır ve yeni ortam işlem kapsamı içinde kendi işlem olur.  
  
 Kapsam ile örneği varsa <xref:System.Transactions.TransactionScopeOption.Suppress>, hiçbir zaman bir işlem içinde bölümü alır, ne olursa olsun, ortam bir işlem olup olmadığını mevcuttur. Bu değer her zaman örneği bir kapsama sahip **null** ortam işlem olarak.  
  
 Yukarıdaki seçenekleri aşağıdaki tabloda özetlenmiştir.  
  
|TransactionScopeOption|Ortam işlem|Kapsam bölümü alır|  
|----------------------------|-------------------------|-----------------------------|  
|Gerekli|Hayır|Yeni bir işlem (kök olacaktır)|  
|Yeni gerektirir|Hayır|Yeni bir işlem (kök olacaktır)|  
|Önle|Hayır|İşlem yok|  
|Gerekli|Evet|Ortam işlem|  
|Yeni gerektirir|Evet|Yeni bir işlem (kök olacaktır)|  
|Önle|Evet|İşlem yok|  
  
 Zaman bir <xref:System.Transactions.TransactionScope> nesne var olan bir ortam işlem birleştirir kapsam nesnesinin atma bitemez işlem işlem kapsam iptalleri sürece. Ortam işlem kök kapsamı tarafından oluşturulmuşsa, yalnızca, kök kapsam silindiğinde mu <xref:System.Transactions.CommittableTransaction.Commit%2A> işleme çağrılmadığı. İşlem el ile oluşturulmuşsa, olduğunda ya da iptal edildi veya oluşturucusu tarafından yürütülen işlemin sona erer.  
  
 Aşağıdaki örnekte gösterildiği bir <xref:System.Transactions.TransactionScope> üç iç içe kapsamlı nesneler, farklı bir her örneklenen oluşturan nesne <xref:System.Transactions.TransactionScopeOption> değeri.  
  
```csharp  
using(TransactionScope scope1 = new TransactionScope())   
//Default is Required   
{   
     using(TransactionScope scope2 = new   
      TransactionScope(TransactionScopeOption.Required))   
     {  
     ...  
     }   
  
     using(TransactionScope scope3 = new TransactionScope(TransactionScopeOption.RequiresNew))   
     {  
     ...  
     }   
  
     using(TransactionScope scope4 = new   
        TransactionScope(TransactionScopeOption.Suppress))   
    {  
     ...  
    }   
}  
```  
  
 Örnek, yeni bir kapsam oluşturma ortam işlem olmadan kod bloğu gösterir (`scope1`) ile <xref:System.Transactions.TransactionScopeOption.Required>. Kapsam `scope1` yeni bir işlem (işlem A) oluşturur ve bir işlem yapar gibi bir kök kapsamı olan ortam işlem. `Scope1`Daha sonra her farklı bir ile üç daha fazla nesne oluşturur <xref:System.Transactions.TransactionScopeOption> değeri. Örneğin, `scope2` ile oluşturulan <xref:System.Transactions.TransactionScopeOption.Required>, hem de ortam bir işlem olduğundan, ilk işlem tarafından oluşturulan birleştirmeleri `scope1`. Unutmayın `scope3` yeni bir işlem ve kök kapsamı `scope4` hiç ortam işlem vardır.  
  
 Değerini varsayılan ve en sık kullanılan olsa da <xref:System.Transactions.TransactionScopeOption> olan <xref:System.Transactions.TransactionScopeOption.Required>, her diğer değerlerinin benzersiz amacı vardır.  
  
 <xref:System.Transactions.TransactionScopeOption.Suppress>kod bölümü tarafından gerçekleştirilen işlemler, korumak istediğiniz ve işlemler başarısız oluyorsa ortam hareketi iptal etmek istiyor musunuz durumlarda faydalıdır. Örneğin, günlük gerçekleştirin veya operations denetlemek istediğinizde ya da bakılmaksızın abonelere olayları yayımlamak istediğiniz ortam işleminiz tamamlandıktan olup durdurur. Bu değer, işlemsel olmayan kod bölümünde bir işlem kapsamı içinde sağlamak aşağıdaki örnekte gösterildiği gibi sağlar.  
  
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
     catch  
     {}  
   //Rest of scope1  
}  
```  
  
### <a name="voting-inside-a-nested-scope"></a>İç içe bir kapsam içinde oylama  
 İç içe geçmiş bir kapsam kök kapsamının ortam işlem katılabilirsiniz rağmen çağırma <xref:System.Transactions.TransactionScope.Complete%2A> iç içe geçmiş kapsamdaki kök kapsamda herhangi bir etkisi yoktur. İşlemi, yalnızca son iç içe geçmiş kapsam aşağıya doğru kök kapsamdan tüm kapsamlar oy verin, işlem uygulanır. Değil çağırma <xref:System.Transactions.TransactionScope.Complete%2A> ortam işlem hemen iptal edilecek gibi iç içe geçmiş kapsamdaki kök kapsam etkiler.  
  
## <a name="setting-the-transactionscope-timeout"></a>TransactionScope zaman aşımını ayarlama  
 Aşırı yüklenmiş oluşturucular bazıları <xref:System.Transactions.TransactionScope> türünde bir değer kabul <xref:System.TimeSpan>, işlem zaman aşımı denetlemek için kullanılır. Sıfır olarak ayarlanmış bir zaman aşımı sonsuz bir zaman aşımı anlamına gelir. Sonsuz bir zaman aşımı kodunuz adımla iş mantığınızı sorunun yalıtmak istediğinizi ve sorunu bulmaya sırasında zaman aşımı için hata ayıklama işlem istiyor musunuz çoğunlukla, hata ayıklama için faydalıdır. İşlem kilitlenmeleri karşı koruma kıldığından diğer durumlarda, sonsuz bir zaman aşımı değerini kullanarak çok dikkatli olun.  
  
 Genellikle ayarlanabilir <xref:System.Transactions.TransactionScope> zaman aşımına uğramak üzere iki durumda da varsayılan dışındaki değerler. Uygulama tanıtıcıları işlemleri durduruldu şekilde test etmek istediğiniz zaman ilk geliştirme sırasında ' dir. Zaman aşımı (örneğin, bir mili saniye) küçük bir değere ayarlayarak, işleminiz başarısız olmasına neden ve böylece hata işleme kodunu görebilirsiniz. Kapsam içinde kaynak talebi, söz konusu kilitlenmeleri kaynaklanan düşünüyorsanız, varsayılan zaman aşımı değerinden bir değere ayarlamanız ikinci durumdur. Bu durumda, işlemin hemen durdurmak ve varsayılan zaman aşımı süresi dolacak şekilde bekleme istiyorsunuz.  
  
 Bir kapsam bir ortam işlem birleştirir halde ortam işlem ayarlanmış olandan daha küçük bir zaman aşımını belirtir, yeni, daha kısa bir zaman aşımı uygulanır <xref:System.Transactions.TransactionScope> nesne ve kapsam belirtilen iç içe geçmiş sürede bitmelidir ya da işlem otomatik olarak iptal edildi. İç içe geçmiş kapsamın zaman aşımı, ortam işlem büyük hiçbir etkisi yoktur.  
  
## <a name="setting-the-transactionscope-isolation-level"></a>TransactionScope yalıtım düzeyini ayarlama  
 Aşırı yüklenmiş oluşturucular bazıları <xref:System.Transactions.TransactionScope> türü yapısını kabul <xref:System.Transactions.TransactionOptions> bir zaman aşımı değeri ek bir yalıtım düzeyini belirtir. Varsayılan olarak, yalıtım düzeyi ayarlamak işlem yürütür <xref:System.Transactions.IsolationLevel.Serializable>. Başka bir yalıtım düzeyi seçme <xref:System.Transactions.IsolationLevel.Serializable> yaygın olarak okuma yoğun sistemleri için kullanılır. Bu işlem teorik ve işlem semantiği, söz konusu eşzamanlılık sorunları ve sistemi tutarlılığı sonuçları işleme düz bir anlayış gerektirir.  
  
 Ayrıca, tüm kaynak yöneticileri tüm yalıtım düzeyini destekler ve yapılandırılmış olandan daha yüksek düzeyde işlemde katılmak getirmeyi tercih edebilirsiniz.  
  
 Her yalıtım düzeyi yanı sıra <xref:System.Transactions.IsolationLevel.Serializable> aynı bilgilerine erişme diğer işlemlerin kaynaklanan tutarsızlık maruz kalabilir. Farklı yalıtım düzeyleri arasındaki farkı biçiminde okunur ve yazma kilitler kullanılır. Bir kilidi, yalnızca işlem Kaynak Yöneticisi'nde verilere erişen veya hareket kaydedilmiş veya iptal kadar tutulması tutulabilir. Eski verimlilik, tutarlılık ikincisi için iyidir. Kilit iki tür ve işlemleri (okuma/yazma) iki tür dört temel yalıtım düzeyi verin. Daha fazla bilgi edinmek için bkz. <xref:System.Transactions.IsolationLevel>.  
  
 Ne zaman kullanarak iç içe geçmiş <xref:System.Transactions.TransactionScope> nesneleri, tüm iç içe geçmiş kapsamlar ortam işlem katılmaya istiyorsanız tam olarak aynı yalıtım düzeyi kullanacak şekilde yapılandırılması gerekir. İç içe bir varsa <xref:System.Transactions.TransactionScope> nesne çalışır farklı yalıtım düzeyi belirtir henüz ortam işlem katılmak bir <xref:System.ArgumentException> oluşturulur.  
  
## <a name="interop-with-com"></a>COM + ile birlikte çalışma  
 Yeni bir oluşturduğunuzda <xref:System.Transactions.TransactionScope> örneğini kullanabilir <xref:System.Transactions.EnterpriseServicesInteropOption> COM + ile etkileşim kurmak nasıl belirlemek için oluşturucular birinde numaralandırması. Bunun hakkında daha fazla bilgi için bkz: [Kurumsal Hizmetler ve COM + işlemleri ile birlikte çalışabilirlik](../../../../docs/framework/data/transactions/interoperability-with-enterprise-services-and-com-transactions.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Transactions.Transaction.Clone%2A>  
 <xref:System.Transactions.TransactionScope>
