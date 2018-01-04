---
title: "Açık bir CommittableTransaction kullanarak işlem uygulama"
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
ms.assetid: 29efe5e5-897b-46c2-a35f-e599a273acc8
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ce77ddab23063588e347073de4d4c25e5fbb5a01
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-an-explicit-transaction-using-committabletransaction"></a>Açık bir CommittableTransaction kullanarak işlem uygulama
<xref:System.Transactions.CommittableTransaction> Sınıfı kullanarak bir işlem kullanmak üzere uygulamalar için açık bir yol sağlar <xref:System.Transactions.TransactionScope> örtük olarak sınıf. Birden çok işlev çağrıları veya birden çok iş parçacığı çağrıları arasında aynı işlem kullanmak istediğiniz uygulamalar için kullanışlıdır. Farklı <xref:System.Transactions.TransactionScope> uygulama yazıcısı sınıfının gerekir özellikle çağırmak <xref:System.Transactions.CommittableTransaction.Commit%2A> ve <xref:System.Transactions.Transaction.Rollback%2A> yürütün veya işlem iptal etmek için yöntemleri.  
  
## <a name="overview-of-the-committabletransaction-class"></a>CommittableTransaction sınıfı genel bakış  
 <xref:System.Transactions.CommittableTransaction> Sınıf türetilir <xref:System.Transactions.Transaction> sınıfı, bu nedenle tüm işlevselliğini ikincisi sağlama. Özellikle yararlıdır <xref:System.Transactions.Transaction.Rollback%2A> yöntemi <xref:System.Transactions.Transaction> geri almak için de kullanılabilir sınıf bir <xref:System.Transactions.CommittableTransaction> nesne.  
  
 <xref:System.Transactions.Transaction> Sınıf benzer <xref:System.Transactions.CommittableTransaction> sınıfının ancak teklif değil bir `Commit` yöntemi. Bu, işlem nesnesini (veya bunu klonlar) diğer yöntemleri (büyük olasılıkla diğer iş parçacıkları) hala hareket kaydedilmiş olduğunda denetleme sırasında geçirilecek sağlar. Çağrılan kodu listeleme ve işlem ancak yalnızca oluşturan oy verin <xref:System.Transactions.CommittableTransaction> nesnenin hareketi olanağı vardır.  
  
 Followings ile çalışırken dikkat etmelisiniz <xref:System.Transactions.CommittableTransaction> sınıfı  
  
-   Oluşturma bir <xref:System.Transactions.CommittableTransaction> işlem ortam işlem ayarlı değil. Özel olarak ayarlayın ve kaynak yöneticileri doğru işlem bağlamı altında uygun olduğunda çalışması emin olmak için ortam işlem sıfırlamak gerekir. Geçerli ortam işlem ayarlamak için statik ayarlayarak yoludur <xref:System.Transactions.Transaction.Current%2A> genel özellikte <xref:System.Transactions.Transaction> nesnesi.  
  
-   Bir <xref:System.Transactions.CommittableTransaction> nesne olamaz yeniden kullanılabilecek. Bir kez bir <xref:System.Transactions.CommittableTransaction> nesne yürütülmeli veya geri, yeniden işlemde kullanılamaz. Diğer bir deyişle, geçerli ortam işlem bağlamı olarak ayarlanamaz.  
  
## <a name="creating-a-committabletransaction"></a>Bir CommittableTransaction oluşturma  
 Aşağıdaki örnek, yeni bir oluşturur <xref:System.Transactions.CommittableTransaction> ve onu kaydeder.  
  
 [!code-csharp[Tx_CommittableTx#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/tx_committabletx/cs/committabletxwithsql.cs#1)]
 [!code-vb[Tx_CommittableTx#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/tx_committabletx/vb/committabletxwithsql.vb#1)]  
  
 Örneği oluşturmayı <xref:System.Transactions.CommittableTransaction> otomatik olarak ortam işlem bağlamı ayarlı değil. Bu nedenle, bir Kaynak Yöneticisi'ni üzerinde herhangi bir işlemi bu işlemin bir parçası değil. Statik <xref:System.Transactions.Transaction.Current%2A> genel özellikte <xref:System.Transactions.Transaction> nesnesi ayarlamak veya ortam işlem almak için kullanılır ve uygulamayı el ile kaynak yöneticileri işlemde katılabilir emin olmak için ayarlamanız gerekir. Eski ortam işlem kaydetme ve kullanarak bitirdikten sonra geri yükleme içinde iyi bir uygulamadır <xref:System.Transactions.CommittableTransaction> nesnesi.  
  
 İşlem gerçekleştirmeyi açıkça çağırması gerekir <xref:System.Transactions.CommittableTransaction.Commit%2A> yöntemi. Bir işlemin geri alınması için çağırmalısınız <xref:System.Transactions.Transaction.Rollback%2A> yöntemi. Başarılı olana dek dikkate almak önemlidir bir <xref:System.Transactions.CommittableTransaction> kabul edildiğini veya işlem hala kilitli, söz konusu tüm kaynakları geri alınamaz.  
  
 Bir <xref:System.Transactions.CommittableTransaction> işlev çağrıları ve dizileri arasında nesne kullanılabilir. Ancak, bu özel durumları işlemek ve özellikle çağırmak için uygulama geliştiricisi kadar kadar <xref:System.Transactions.Transaction.Rollback%28System.Exception%29> yöntemi hataları durumunda.  
  
## <a name="asynchronous-commit"></a>Zaman uyumsuz tamamlama  
 <xref:System.Transactions.CommittableTransaction> Sınıfı zaman uyumsuz bir işlem gerçekleştirmeden için bir mekanizma sağlar. Birden çok veritabanı erişimi ve olası ağ gecikmesi gerektirebilir gibi bir işlem yürütme önemli ölçüde zaman alabilir. Yüksek verimlilik uygulamalarında kilitlenmeleri yapmak istemiyorsanız, işlem iş mümkün olan en kısa sürede tamamlamak için zaman uyumsuz tamamlama kullanın ve yürütme işlemi bir arka plan görevi olarak çalıştırın. <xref:System.Transactions.CommittableTransaction.BeginCommit%2A> Ve <xref:System.Transactions.CommittableTransaction.EndCommit%2A> yöntemlerinin <xref:System.Transactions.CommittableTransaction> sınıfı, bunu yapmak izin.  
  
 Çağırabilirsiniz <xref:System.Transactions.CommittableTransaction.BeginCommit%2A> yürütme Soyguncu iş parçacığı havuzu için bir iş parçacığı gönderme. Ayrıca, çağırabilirsiniz <xref:System.Transactions.CommittableTransaction.EndCommit%2A> işlem gerçekte kaydedilmiş olup olmadığını belirlemek için. İşlem herhangi bir nedenle başarısız oldu, <xref:System.Transactions.CommittableTransaction.EndCommit%2A> bir işlem özel durumu oluşturur. İşlem henüz zamanına göre gerçekleştirilir değil, <xref:System.Transactions.CommittableTransaction.EndCommit%2A> olduğu adlı hareket kaydedilmiş veya iptal kadar arayan engellendi.  
  
 Bir zaman uyumsuz tamamlama yapmak için kolay Sistemi'ne tamamlandığında çağrılacak bir geri çağırma yöntemi sağlayarak yoludur. Ancak, çağırmalıdır <xref:System.Transactions.CommittableTransaction.EndCommit%2A> özgün yöntemini <xref:System.Transactions.CommittableTransaction> arama çağırmak için kullanılan nesne. Bu nesne elde etmek için alta yapabilecekleriniz *IAsyncResult* geri çağırma yöntemi parametresinin beri <xref:System.Transactions.CommittableTransaction> sınıfını uygular <xref:System.IAsyncResult> sınıfı.  
  
 Aşağıdaki örnek, bir zaman uyumsuz tamamlama nasıl yapılacağı gösterir.  
  
```csharp  
public void DoTransactionalWork()  
{  
     Transaction oldAmbient = Transaction.Current;  
     CommittableTransaction committableTransaction = new CommittableTransaction();  
     Transaction.Current = committableTransaction;  
  
     try  
     {  
          /* Perform transactional work here */  
          // No errors - commit transaction asynchronously  
          committableTransaction.BeginCommit(OnCommitted,null);  
     }  
     finally  
     {  
          //Restore the ambient transaction   
          Transaction.Current = oldAmbient;  
     }  
}  
void OnCommitted(IAsyncResult asyncResult)  
{  
     CommittableTransaction committableTransaction;  
     committableTransaction = asyncResult as CommittableTransaction;     
     Debug.Assert(committableTransaction != null);  
     try  
     {  
          using(committableTransaction)  
          {  
               committableTransaction.EndCommit(asyncResult);  
          }  
     }  
     catch(TransactionException e)  
     {  
          //Handle the failure to commit  
     }  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İşlem Kapsamı Kullanarak Örtük İşlem Uygulama](../../../../docs/framework/data/transactions/implementing-an-implicit-transaction-using-transaction-scope.md)  
 [İşlem Gerçekleştirme](../../../../docs/framework/data/transactions/index.md)
