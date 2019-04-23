---
title: CommittableTransaction Kullanarak Belirtik İşlem Uygulama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 29efe5e5-897b-46c2-a35f-e599a273acc8
ms.openlocfilehash: 1a02520ab7d1196b8071bda752ae30896958f372
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59105423"
---
# <a name="implementing-an-explicit-transaction-using-committabletransaction"></a>CommittableTransaction Kullanarak Belirtik İşlem Uygulama
<xref:System.Transactions.CommittableTransaction> Sınıfı sağlar sınıfını kullanarak bir işlem kullanmak uygulamalar için açık bir yol <xref:System.Transactions.TransactionScope> örtülü olarak sınıf. Birden fazla işlev çağrıları veya birden çok iş parçacığı çağrı aynı işlem kullanmak istediğiniz uygulamalar için yararlıdır. Farklı <xref:System.Transactions.TransactionScope> sınıfı, uygulama yazıcı gerekiyor özellikle çağrılacak <xref:System.Transactions.CommittableTransaction.Commit%2A> ve <xref:System.Transactions.Transaction.Rollback%2A> tamamlama veya işlem iptal için yöntemleri.  
  
## <a name="overview-of-the-committabletransaction-class"></a>CommittableTransaction sınıfı genel bakış  
 <xref:System.Transactions.CommittableTransaction> Sınıf türetilir <xref:System.Transactions.Transaction> sınıfı, bu nedenle tüm işlevselliğini ikincisi sağlama. Özellikle yararlıdır <xref:System.Transactions.Transaction.Rollback%2A> yöntemi <xref:System.Transactions.Transaction> geri almak için de kullanılabilir sınıf bir <xref:System.Transactions.CommittableTransaction> nesne.  
  
 <xref:System.Transactions.Transaction> Sınıf benzer <xref:System.Transactions.CommittableTransaction> sınıfının ancak teklif değil bir `Commit` yöntemi. Bu işlem nesnesi (veya bunun kopyalar) diğer yöntemleri (büyük olasılıkla diğer iş parçacıkları) için işlem taahhüt olduğunda hala denetleme sırasında geçirmenizi sağlar. Çağrılan listeleme ve işlem ancak yalnızca oluşturan oy kodudur <xref:System.Transactions.CommittableTransaction> nesnenin hareketi olanağı vardır.  
  
 Followings ile çalışırken dikkat etmelisiniz <xref:System.Transactions.CommittableTransaction> sınıfı  
  
-   Oluşturma bir <xref:System.Transactions.CommittableTransaction> işlem ortam işlem ayarlı değil. Özel olarak ayarlayın ve kaynak yöneticileri sağ işlem bağlamında uygun olduğunda çalıştırmak emin olmak için ortam işlem sıfırlamak gerekir. Geçerli ortam hareket ayarlamak için statik ayarlayarak yoludur <xref:System.Transactions.Transaction.Current%2A> özelliği genel <xref:System.Transactions.Transaction> nesne.  
  
-   Bir <xref:System.Transactions.CommittableTransaction> nesne olamaz yeniden kullanılabilecek. Bir kez bir <xref:System.Transactions.CommittableTransaction> nesne kaydedilmiş veya geri alınmış, bir işlemde yeniden kullanılamaz. Diğer bir deyişle, geçerli ortam işlem bağlamı olarak ayarlanamaz.  
  
## <a name="creating-a-committabletransaction"></a>Bir CommittableTransaction oluşturma  
 Aşağıdaki örnek, yeni bir oluşturur <xref:System.Transactions.CommittableTransaction> ve onu kaydeder.  
  
 [!code-csharp[Tx_CommittableTx#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/tx_committabletx/cs/committabletxwithsql.cs#1)]
 [!code-vb[Tx_CommittableTx#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/tx_committabletx/vb/committabletxwithsql.vb#1)]  
  
 Bir örneğini oluşturmaktan <xref:System.Transactions.CommittableTransaction> ortam işlem bağlamı otomatik olarak ayarlanmadı. Bu nedenle, bir kaynak yöneticisi üzerinde herhangi bir işlemi bu işlemin bir parçası değil. Statik <xref:System.Transactions.Transaction.Current%2A> özelliği genel <xref:System.Transactions.Transaction> nesnesi ortam işlem almak veya ayarlamak için kullanılır ve uygulama el ile kaynak yöneticileri işlem sırasında katılabilir emin olmak için ayarlamanız gerekir. Eski ortam işlem kaydedin ve kullanmayı bitirdiğinizde geri içinde iyi bir uygulamadır <xref:System.Transactions.CommittableTransaction> nesne.  
  
 Hareketi tamamlamak için açıkça çağırmak ihtiyacınız <xref:System.Transactions.CommittableTransaction.Commit%2A> yöntemi. Bir işlemin geri alınması için çağırmalısınız <xref:System.Transactions.Transaction.Rollback%2A> yöntemi. Unutmayın kadar önemlidir bir <xref:System.Transactions.CommittableTransaction> kaydedilmiş veya işlem hala kilitli olduğunu, tüm kaynaklardan döndürülmesine.  
  
 Bir <xref:System.Transactions.CommittableTransaction> işlev çağrıları ve dizileri arasında nesne kullanılabilir. Ancak, bu özel durumları işlemek ve özellikle çağırmak için uygulama geliştiricisi kadar kadar <xref:System.Transactions.Transaction.Rollback%28System.Exception%29> yöntemi hataları durumunda.  
  
## <a name="asynchronous-commit"></a>Zaman uyumsuz tamamlama  
 <xref:System.Transactions.CommittableTransaction> Sınıfı zaman uyumsuz bir işlem Sistemi'ne yönelik bir mekanizma sağlar. Birden çok veritabanı erişimi ve olası ağ gecikmesi gerektirebilir gibi bir işlem kaydı önemli ölçüde uzun sürebilir. Yüksek verimlilik uygulamalarında kilitlenmeleri önlemek istediğinizde, işlem iş sürede tamamlamak için zaman uyumsuz tamamlama kullanın ve yürütme işlemini bir arka plan görevini çalıştırın. <xref:System.Transactions.CommittableTransaction.BeginCommit%2A> Ve <xref:System.Transactions.CommittableTransaction.EndCommit%2A> yöntemlerinin <xref:System.Transactions.CommittableTransaction> sınıfı, bunu yapmak izin.  
  
 Çağırabilirsiniz <xref:System.Transactions.CommittableTransaction.BeginCommit%2A> yürütme Soyguncu iş parçacığı havuzu için bir iş parçacığı gönderme. Ayrıca, çağırabilirsiniz <xref:System.Transactions.CommittableTransaction.EndCommit%2A> işlem gerçekten kaydedildi, belirlemek için. İşlem teslim herhangi bir nedenle başarısız olursa <xref:System.Transactions.CommittableTransaction.EndCommit%2A> işlem özel durumu oluşturur. İşlem henüz zaman teslim edilmemiş varsa <xref:System.Transactions.CommittableTransaction.EndCommit%2A> olduğunu hareket kaydedilmiş veya iptal kadar çağrılır, çağrıyı yapan engellenir.  
  
 Bir zaman uyumsuz tamamlama yapmak için kolay Sistemi'ne tamamlandığında çağrılacak bir geri çağırma yöntemi sağlayarak yoludur. Ancak, çağırmalıdır <xref:System.Transactions.CommittableTransaction.EndCommit%2A> özgün yöntemini <xref:System.Transactions.CommittableTransaction> arama çağırmak için kullanılan nesne. Bu nesne elde etmek üzere alta yapabilecekleriniz *IAsyncResult* geri çağırma yöntemi parametresinin bu yana <xref:System.Transactions.CommittableTransaction> sınıfının Implements <xref:System.IAsyncResult> sınıfı.  
  
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

- [İşlem Kapsamı Kullanarak Örtük İşlem Uygulama](../../../../docs/framework/data/transactions/implementing-an-implicit-transaction-using-transaction-scope.md)
- [İşlem Gerçekleştirme](../../../../docs/framework/data/transactions/index.md)
