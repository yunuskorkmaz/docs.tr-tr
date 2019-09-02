---
title: CommittableTransaction Kullanarak Belirtik İşlem Uygulama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 29efe5e5-897b-46c2-a35f-e599a273acc8
ms.openlocfilehash: 19b62c24d00903d1494a755dbeabb460935cdacd
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205934"
---
# <a name="implementing-an-explicit-transaction-using-committabletransaction"></a>CommittableTransaction Kullanarak Belirtik İşlem Uygulama
Sınıfı, uygulamaların bir işlem kullanması için açık bir yol sağlar, bu da <xref:System.Transactions.TransactionScope> sınıfı örtülü olarak kullanmaktır. <xref:System.Transactions.CommittableTransaction> Birden çok işlev çağrısı veya birden çok iş parçacığı çağrısı genelinde aynı işlemi kullanmak isteyen uygulamalar için yararlıdır. Sınıfının aksine, uygulama yazıcısının işlem yürütmek veya durdurmak için özel olarak <xref:System.Transactions.CommittableTransaction.Commit%2A> ve <xref:System.Transactions.Transaction.Rollback%2A> yöntemlerini çağırması gerekir. <xref:System.Transactions.TransactionScope>  
  
## <a name="overview-of-the-committabletransaction-class"></a>CommittableTransaction sınıfına genel bakış  
 <xref:System.Transactions.CommittableTransaction> Sınıf türetilir <xref:System.Transactions.Transaction> sınıfı, bu nedenle tüm işlevselliğini ikincisi sağlama. Özellikle yararlıdır <xref:System.Transactions.Transaction.Rollback%2A> yöntemi <xref:System.Transactions.Transaction> geri almak için de kullanılabilir sınıf bir <xref:System.Transactions.CommittableTransaction> nesne.  
  
 <xref:System.Transactions.Transaction> Sınıf benzer <xref:System.Transactions.CommittableTransaction> sınıfının ancak teklif değil bir `Commit` yöntemi. Bu işlem, işlemin ne zaman planlanmakta olduğunu denetlerken, işlem nesnesini (veya bunların klonlarını) diğer yöntemlere (potansiyel olarak diğer iş parçacıklarında) geçirmenize olanak sağlar. Çağrılan kod, işlem üzerinde listeleme ve oy verebilir, ancak yalnızca <xref:System.Transactions.CommittableTransaction> nesnenin Oluşturucusu işlemi işleme olanağına sahiptir.  
  
 Followings ile çalışırken dikkat etmelisiniz <xref:System.Transactions.CommittableTransaction> sınıfı  
  
- <xref:System.Transactions.CommittableTransaction> İşlem oluşturmak çevresel işlem yapmaz. Kaynak yöneticilerinin uygun olduğunda doğru işlem bağlamında çalışmasını sağlamak için, ortam işlemini özellikle ayarlamanız ve sıfırlamanız gerekir. Geçerli ortam işlemini ayarlama yöntemi, genel <xref:System.Transactions.Transaction.Current%2A> <xref:System.Transactions.Transaction> nesnede statik özelliği ayarlamadır.  
  
- Bir <xref:System.Transactions.CommittableTransaction> nesne olamaz yeniden kullanılabilecek. Bir <xref:System.Transactions.CommittableTransaction> nesne kaydedildikten veya geri alındıktan sonra, bir işlem içinde yeniden kullanılamaz. Diğer bir deyişle, geçerli ortam işlem bağlamı olarak ayarlanamaz.  
  
## <a name="creating-a-committabletransaction"></a>CommittableTransaction oluşturma  
 Aşağıdaki örnek, yeni bir oluşturur <xref:System.Transactions.CommittableTransaction> ve onu kaydeder.  
  
 [!code-csharp[Tx_CommittableTx#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/tx_committabletx/cs/committabletxwithsql.cs#1)]
 [!code-vb[Tx_CommittableTx#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/tx_committabletx/vb/committabletxwithsql.vb#1)]  
  
 Bir örneğinin <xref:System.Transactions.CommittableTransaction> oluşturulması, ortam işlem bağlamını otomatik olarak yapmaz. Bu nedenle, bir kaynak yöneticisi üzerinde herhangi bir işlem bu işlemin bir parçası değildir. <xref:System.Transactions.Transaction.Current%2A> Genel<xref:System.Transactions.Transaction> nesnedeki static özelliği, ortam işlemini ayarlamak ya da almak için kullanılır ve uygulama, kaynak yöneticilerinin işleme katılmasını sağlamak için el ile ayarlamanız gerekir. Ayrıca, eski çevresel işlemi kaydetmek ve <xref:System.Transactions.CommittableTransaction> nesneyi kullanmayı bitirdiğinizde geri yüklemek iyi bir uygulamadır.  
  
 İşlemi yürütmek için <xref:System.Transactions.CommittableTransaction.Commit%2A> yöntemi açıkça çağırmanız gerekir. Bir işlemi geri almak için <xref:System.Transactions.Transaction.Rollback%2A> yöntemini çağırmanız gerekir. Bir <xref:System.Transactions.CommittableTransaction> işlem kaydedilene veya geri alınana kadar, bu işlemde yer alan tüm kaynakların hala kilitli olduğuna dikkat edin.  
  
 Bir <xref:System.Transactions.CommittableTransaction> işlev çağrıları ve dizileri arasında nesne kullanılabilir. Ancak, bu özel durumları işlemek ve özellikle çağırmak için uygulama geliştiricisi kadar kadar <xref:System.Transactions.Transaction.Rollback%28System.Exception%29> yöntemi hataları durumunda.  
  
## <a name="asynchronous-commit"></a>Zaman uyumsuz tamamlama  
 <xref:System.Transactions.CommittableTransaction> Sınıfı ayrıca bir işlemi zaman uyumsuz olarak yürütmek için bir mekanizma sağlar. Bir işlem işleme, birden çok veritabanı erişimi ve olası ağ gecikmesi olabileceği için önemli ölçüde zaman alabilir. Yüksek performanslı uygulamalarda kilitlenmeleri önlemek istediğinizde, işlem işini en kısa sürede tamamlamak için zaman uyumsuz yürütmeyi kullanabilir ve tamamlama işlemini bir arka plan görevi olarak çalıştırabilirsiniz. <xref:System.Transactions.CommittableTransaction.BeginCommit%2A> Ve <xref:System.Transactions.CommittableTransaction.EndCommit%2A> yöntemlerinin <xref:System.Transactions.CommittableTransaction> sınıfı, bunu yapmak izin.  
  
 Çağırabilirsiniz <xref:System.Transactions.CommittableTransaction.BeginCommit%2A> yürütme Soyguncu iş parçacığı havuzu için bir iş parçacığı gönderme. İşlemin gerçekten kaydedilmiş olup <xref:System.Transactions.CommittableTransaction.EndCommit%2A> olmadığını belirleme çağrısı yapabilirsiniz. İşlem herhangi bir nedenden dolayı işleme başarısız olursa, <xref:System.Transactions.CommittableTransaction.EndCommit%2A> bir işlem özel durumu oluşturur. İşlem henüz zamana <xref:System.Transactions.CommittableTransaction.EndCommit%2A> göre yürütülmemişse, işlem kaydedilene veya durduruluncaya kadar çağrı engellenir.  
  
 Bir zaman uyumsuz tamamlama yapmak için kolay Sistemi'ne tamamlandığında çağrılacak bir geri çağırma yöntemi sağlayarak yoludur. Ancak, çağırmalıdır <xref:System.Transactions.CommittableTransaction.EndCommit%2A> özgün yöntemini <xref:System.Transactions.CommittableTransaction> arama çağırmak için kullanılan nesne. Bu nesneyi almak için, <xref:System.Transactions.CommittableTransaction> sınıf sınıfı uyguladığı <xref:System.IAsyncResult> için geri çağırma yönteminin *IAsyncResult* parametresini alt türe dönüştürebilirsiniz.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [İşlem Kapsamı Kullanarak Örtük İşlem Uygulama](implementing-an-implicit-transaction-using-transaction-scope.md)
- [İşlem Gerçekleştirme](index.md)
