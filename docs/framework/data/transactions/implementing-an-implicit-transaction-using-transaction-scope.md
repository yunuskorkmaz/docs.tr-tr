---
title: İşlem Kapsamı Kullanarak Örtük İşlem Uygulama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49d1706a-1e0c-4c85-9704-75c908372eb9
ms.openlocfilehash: e9e5e09bdde82c7b818fd47275bdbfeda5850682
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645751"
---
# <a name="implementing-an-implicit-transaction-using-transaction-scope"></a>İşlem Kapsamı Kullanarak Örtük İşlem Uygulama
<xref:System.Transactions.TransactionScope> Sınıfı bir işlem ile etkileşime gerek kalmadan bir işlemde katılan olarak kod bloğu işaretlemek için basit bir yol sağlar. İşlem kapsamı seçebilir ve ortam işlem otomatik olarak yönetir. Kendi kullanım kolaylığı ve verimliliği nedeniyle, kullanmanız önerilir <xref:System.Transactions.TransactionScope> sınıfı bir işlem uygulama geliştirirken.  
  
 Ayrıca, işlem açıkça kaynaklarla listeleme gerekmez. Tüm <xref:System.Transactions> Kaynak Yöneticisi (örneğin, SQL Server 2005) kapsam tarafından oluşturulan bir ortam hareket varlığını algılayabilir ve otomatik olarak listeleme.  
  
## <a name="creating-a-transaction-scope"></a>İşlem kapsamı oluşturma  
 Aşağıdaki örnek, bir basit kullanımını gösterir <xref:System.Transactions.TransactionScope> sınıfı.  
  
 [!code-csharp[TransactionScope#1](../../../../samples/snippets/csharp/VS_Snippets_Remoting/TransactionScope/cs/ScopeWithSQL.cs#1)]
 [!code-vb[TransactionScope#1](../../../../samples/snippets/visualbasic/VS_Snippets_Remoting/TransactionScope/vb/ScopeWithSQL.vb#1)]  
  
 Yeni bir oluşturduktan sonra işlem kapsamı başlatılır <xref:System.Transactions.TransactionScope> nesne.  Kod örneğinde gösterildiği gibi kapsamlar ile oluşturmanız önerilir bir **kullanarak** deyimi. **Kullanarak** deyimi kullanılabilir her ikisinde de C# ve Visual Basic ve gibi çalışır bir **try... finally** blok kapsamı, düzgün bir şekilde elden emin olmak için.  
  
 Ne zaman örneği <xref:System.Transactions.TransactionScope>, hareket yöneticisi katılmak için hangi işlem belirler. Belirlenen sonra kapsam her zaman bu harekete katılan. Karar iki etkene dayanır: bir ortam işlem mevcut olup olmadığını ve değerini **TransactionScopeOption** oluşturucuda parametresi. Ortam işlem içinde kodunuzu yürütür işlem bir işlemdir. Statik çağırarak bir başvuru ortam işlem edinebilirsiniz <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType> özelliği <xref:System.Transactions.Transaction> sınıfı. Bu parametre nasıl kullanıldığı hakkında daha fazla bilgi için bkz: [işlem akışı TransactionScopeOption kullanarak yönetme](#ManageTxFlow) bu konudaki.  
  
## <a name="completing-a-transaction-scope"></a>İşlem kapsamı Tamamlanıyor  
 Uygulamanızı tüm iş tamamlandığında bir işlemde gerçekleştirmek istediği, çağırması gerekir <xref:System.Transactions.TransactionScope.Complete%2A?displayProperty=nameWIthType> hareketi tamamlamak için uygun olduğunu hareket yöneticisi bilgilendirmek için yalnızca bir kez yöntemi. Çağrı yerleştirmek için çok iyi bir uygulamadır <xref:System.Transactions.TransactionScope.Complete%2A> son ifade olarak **kullanarak** blok.  
  
 Çünkü bu bir sistem hatası veya işlem kapsamında oluşturulan bir özel eşdeğer olarak yorumlar hareket yöneticisi bu yöntemini çağırmak başarısız olan işlemi durdurur. Ancak, bu yöntemi çağırmadan, işlem garanti etmez wil taahhüt. İşlem Yöneticisi durumunuzu bildiren yalnızca bir yoludur. Arama sonra <xref:System.Transactions.TransactionScope.Complete%2A> yöntemini kullanarak artık ortam işlem erişebilirsiniz <xref:System.Transactions.Transaction.Current%2A> özelliği ve bunu yapma girişimi oluşturulan bir özel durum neden olur.  
  
 Varsa <xref:System.Transactions.TransactionScope> işlem başlangıçta oluşturulan işlem hareket yöneticisi tarafından Sistemi'ne gerçek işini gerçekleşir kodda son satırının sonra nesnesi **kullanarak** blok. İşlem oluşturmadıysanız, yürütme zaman meydana gelir <xref:System.Transactions.CommittableTransaction.Commit%2A> sahibi tarafından çağrılır <xref:System.Transactions.CommittableTransaction> nesne. Bu noktada işlem yöneticisi kaynak yöneticileri çağırır ve yürütme veya geri alma, yoksa tabanlı bildiren <xref:System.Transactions.TransactionScope.Complete%2A> yöntemi çağrıldı <xref:System.Transactions.TransactionScope> nesne.  
  
 **Kullanarak** bildirimi sağlar <xref:System.Transactions.TransactionScope.Dispose%2A> yöntemi <xref:System.Transactions.TransactionScope> nesne bile özel bir durum oluştuğunda çağrılır. <xref:System.Transactions.TransactionScope.Dispose%2A> Yöntemi işlem kapsamı sonunu işaretler. Bu yöntemi çağrıldıktan sonra oluşan özel durumlarının işlem etkileyebilir değil. Bu yöntem aynı zamanda ortam işlem için önceki durumuna geri yükler.  
  
 A <xref:System.Transactions.TransactionAbortedException> işlem kapsamı oluşturur ve işlem iptal oluşturulur. A <xref:System.Transactions.TransactionInDoubtException> hareket yöneticisi tamamlama karar bağlanamazsa, oluşturulur. İşlem, hiçbir özel durum oluşturulur.  
  
## <a name="rolling-back-a-transaction"></a>Bir işlemi geri alınıyor  
 Bir işlem geri almak istiyorsanız, değil, çağırmalıdır <xref:System.Transactions.TransactionScope.Complete%2A> işlem kapsamında yöntemi. Örneğin, kapsam içinde bir özel durum. İçinde yer aldığı işlem geri alınacaktır.  
  
## <a name="ManageTxFlow"></a> İşlem akışı TransactionScopeOption kullanarak yönetme  
 İşlem kapsamı kullanan bir yöntem çağrılarak iç içe geçirilemez bir <xref:System.Transactions.TransactionScope> gelen kendi kapsamı kullanan bir yöntem içinde olarak değil durumuyla `RootMethod` aşağıdaki örnekte, yöntemi  
  
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
  
 <xref:System.Transactions.TransactionScope> Sınıf türü numaralandırması kabul birden fazla aşırı yüklü oluşturucular sağlar <xref:System.Transactions.TransactionScopeOption>, kapsam işlem davranışını tanımlar.  
  
 Bir <xref:System.Transactions.TransactionScope> nesnenin üç seçenek vardır:  
  
- Ortam işlem katılın veya bir mevcut değilse yeni bir tane oluşturun.  
  
- Yeni bir kök kapsam, diğer bir deyişle, yeni bir hareket başlatır ve yeni bir ortam işlem kendi kapsam içinde olması bu işlem olmalıdır.  
  
- Bir işlemde hiç katılmak değil. Sonuç olarak ortam hiçbir işlem yok.  
  
 Kapsamı ile örneği varsa <xref:System.Transactions.TransactionScopeOption.Required>ve bir ortam işlem varsa, bu işlem kapsamı birleştirir. Öte yandan, varsa, ortam hiçbir işlem, ardından kapsam yeni bir işlem oluşturur ve kök kapsam haline gelir. Varsayılan değer budur. Zaman <xref:System.Transactions.TransactionScopeOption.Required> olan kullanıldığında, kapsam içinde kod kök olup farklı davranır gerekmez veya yalnızca ortam işlem katılma. Her iki durumda da aynı şekilde çalışması.  
  
 Kapsamı ile örneği varsa <xref:System.Transactions.TransactionScopeOption.RequiresNew>, her zaman bir kök kapsam olur. Yeni bir hareket başlatır ve yeni bir ortam işlem kapsam içinde kendi işlem olur.  
  
 Kapsamı ile örneği varsa <xref:System.Transactions.TransactionScopeOption.Suppress>, hiçbir zaman bir işlemde bölümü alır, bakılmaksızın ortam bir işlem olup olmadığını yok. Bu değeri her zaman örneği bir kapsama sahip **null** ortam kendi işlem olarak.  
  
 Yukarıdaki seçenekleri aşağıdaki tabloda özetlenmiştir.  
  
|TransactionScopeOption|Ortam işlem|Kapsam bölümü alır|  
|----------------------------|-------------------------|-----------------------------|  
|Gerekli|Hayır|Yeni bir işlem (kök olacaktır)|  
|Yeni gerektirir|Hayır|Yeni bir işlem (kök olacaktır)|  
|Önle|Hayır|İşlem yok|  
|Gerekli|Evet|Ortam işlem|  
|Yeni gerektirir|Evet|Yeni bir işlem (kök olacaktır)|  
|Önle|Evet|İşlem yok|  
  
 Olduğunda bir <xref:System.Transactions.TransactionScope> nesne birleştirir varolan bir ortam işlem kapsam nesnesinin elden değil sona erdi işlem sürece işlem kapsamı durdurur. Ortam işlem kök kapsam tarafından oluşturulmuş olsa bile, yalnızca, kök kapsam çıkarıldığından yok <xref:System.Transactions.CommittableTransaction.Commit%2A> işlem çağrılmadığı. İşlem el ile oluşturulmuş olsa bile, olduğunda ya da iptal veya oluşturucusu tarafından kaydedilen işlemi sonlandırır.  
  
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
  
 Örnek kod bloğu yeni bir kapsam oluşturma ortam işlem gösterir (`scope1`) ile <xref:System.Transactions.TransactionScopeOption.Required>. Kapsam `scope1` (bir işlem) yeni bir işlem oluşturur ve işlem yapar gibi bir kök kapsamı olan ortam işlem. `Scope1`Daha sonra her farklı bir ile üç daha fazla nesne oluşturur <xref:System.Transactions.TransactionScopeOption> değeri. Örneğin, `scope2` ile oluşturulan <xref:System.Transactions.TransactionScopeOption.Required>, ve bir ortam işlem olduğundan, onu oluşturan ilk işlem birleştirir `scope1`. Unutmayın `scope3` yeni bir işlem ve kök kapsamı `scope4` ortam hiçbir işlem sahiptir.  
  
 Değerini varsayılan ve en sık kullanılan olsa da <xref:System.Transactions.TransactionScopeOption> olan <xref:System.Transactions.TransactionScopeOption.Required>, her diğer değerlerinin benzersiz amacı vardır.  
  
 <xref:System.Transactions.TransactionScopeOption.Suppress> kod bölümü tarafından gerçekleştirilen işlemleri korumak istediğiniz ve işlemleri başarısız olursa ortam işlemi durdurmak istiyor musunuz yararlı olur. Örneğin, günlük gerçekleştirmek veya işlemlerini denetleme istediğinizde veya bağımsız olarak abonelere olayları yayımlamak istediğiniz olup ortam işleminizin tamamlar veya durdurur. Bu değer, aşağıdaki örnekte gösterildiği gibi bir işlem kapsam içinde bir işlem olmayan kod bölümünde sahip olmanızı sağlar.  
  
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
 Kök kapsamın ortam işlem bir iç içe kapsamı katılabilir olsa da, çağırma <xref:System.Transactions.TransactionScope.Complete%2A> iç içe kapsam içinde kök kapsamına herhangi bir etkisi yoktur. Yalnızca hareketi tamamlamak için son iç içe kapsam kök kapsam tüm kapsamlardan oy, işlem taahhüt olacaktır. Değil çağırma <xref:System.Transactions.TransactionScope.Complete%2A> hemen ortam işlem durdurulacak gibi bir iç içe kapsamda kök kapsam etkiler.  
  
## <a name="setting-the-transactionscope-timeout"></a>TransactionScope zaman aşımı ayarını  
 Bazı aşırı yüklü oluşturucular <xref:System.Transactions.TransactionScope> türünde bir değer kabul <xref:System.TimeSpan>, işlem zaman aşımını denetlemek için kullanılır. Sıfır olarak ayarlanmış bir zaman aşımı sonsuz bir zaman aşımı anlamına gelir. Bir sorun iş mantığınızı, kod içerisinde ilerlemeye tarafından yalıtmak istediğiniz ve sorun bulmaya sırada zaman aşımı için hata ayıklama işlem istiyor musunuz sonsuz zaman aşımı çoğunlukla hata ayıklama için yararlı olur. Bu işlem kilitlenmeleri karşı koruma geçersiz kılar çünkü diğer durumlarda, sonsuz zaman aşımı değerini kullanarak son derece dikkatli olun.  
  
 Genellikle ayarlanabilir <xref:System.Transactions.TransactionScope> zaman aşımına uğramak üzere iki durumda da varsayılan dışındaki değerler. İlk uygulama işleyen durdurulan işlemleri şekilde test etmek istediğiniz geliştirme sırasında andır. Zaman aşımı (örneğin, bir milisaniye) küçük bir değere ayarlayarak, işlem başarısız olmasına neden ve bu nedenle hata işleme kodunu görebilirsiniz. Kapsam içinde kaynak talebi, söz konusu kilitlenmeleri kaynaklanan düşünüyorsanız, varsayılan zaman aşımı değerinden bir değere ayarlamanız ikinci durumdur. Bu durumda, işlem sürede durdurma ve varsayılan zaman aşımı sona bekleyin değil istediğiniz.  
  
 Bir kapsam bir ortam işlem birleştirir halde ortam işlem ayarı daha küçük bir zaman aşımını belirtir, üzerinde yeni ve daha kısa zaman aşımı uygulanır <xref:System.Transactions.TransactionScope> nesnesi ve kapsam içinde iç içe belirlenen zaman bitmelidir veya işlem otomatik olarak durduruldu. İç içe kapsamın zaman aşımı, ortam işlem birden fazla ise, etkiye sahip değildir.  
  
## <a name="setting-the-transactionscope-isolation-level"></a>TransactionScope yalıtım düzeyi ayarlama  
 Bazı aşırı yüklü oluşturucular <xref:System.Transactions.TransactionScope> türünden bir yapıyı kabul <xref:System.Transactions.TransactionOptions> bir zaman aşımı değeri yanı sıra bir yalıtım düzeyi belirtmek için. Varsayılan olarak, ile yalıtım düzeyi ayarlanan işlem yürütür <xref:System.Transactions.IsolationLevel.Serializable>. Başka bir yalıtım düzeyi seçme <xref:System.Transactions.IsolationLevel.Serializable> yaygın olarak okuma yoğun sistemleri için kullanılır. Bu işlem teorik ve işlem semantiği, ilgili eşzamanlılık konuları ve sistem tutarlılık için sonuçlarıyla işleme düz bir anlayış gerektirir.  
  
 Ayrıca, tüm kaynak yöneticileri yalıtım tüm düzeyleri desteği ve daha yüksek bir düzeyde yapılandırılmış bir işlemde katılmak bırakmayı.  
  
 Her yalıtım düzeyi yanı sıra <xref:System.Transactions.IsolationLevel.Serializable> aynı bilgilerine erişmek diğer işlemlerden kaynaklanan tutarsızlık getiriyor. Farklı yalıtım düzeyleri arasındaki farkı biçiminde okunur ve yazma kilitler kullanılır. Kilit yalnızca Veri Kaynağı Yöneticisi'nde işlem erişen veya hareket kaydedilmiş veya iptal kadar tutulması tutulur. Eski verimlilik, tutarlılık ikincisi için iyidir. Kilit iki tür ve işlemleri (okuma/yazma) iki tür dört temel yalıtım düzeyi verin. Daha fazla bilgi edinmek için bkz. <xref:System.Transactions.IsolationLevel>.  
  
 Ne zaman kullanarak içe <xref:System.Transactions.TransactionScope> nesneleri, tüm iç içe kapsamları ortam işlem katılmaya istiyorsanız tam olarak aynı yalıtım düzeyi kullanmak üzere yapılandırılması gerekir. Bir iç içe varsa <xref:System.Transactions.TransactionScope> nesne çalışır bir farklı yalıtım düzeyini belirtir henüz ortam işlem katılmak bir <xref:System.ArgumentException> oluşturulur.  
  
## <a name="interop-with-com"></a>COM + ile birlikte çalışma  
 Yeni bir oluşturduğunuzda <xref:System.Transactions.TransactionScope> kullanabileceğiniz örnek <xref:System.Transactions.EnterpriseServicesInteropOption> oluşturucular nasıl etkileşime COM + ile belirlemek için bir sabit listesi. Bunun hakkında daha fazla bilgi için bkz. [Kurumsal Hizmetler ve COM + işlemleri ile birlikte çalışabilirlik](../../../../docs/framework/data/transactions/interoperability-with-enterprise-services-and-com-transactions.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Transactions.Transaction.Clone%2A>
- <xref:System.Transactions.TransactionScope>
