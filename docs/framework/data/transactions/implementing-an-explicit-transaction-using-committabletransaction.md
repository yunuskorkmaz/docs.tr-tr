---
title: CommittableTransaction Kullanarak Belirtik İşlem Uygulama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 29efe5e5-897b-46c2-a35f-e599a273acc8
ms.openlocfilehash: f8db79db6c4a66dfe13ec936313c4cf2c3b93be5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174413"
---
# <a name="implementing-an-explicit-transaction-using-committabletransaction"></a>CommittableTransaction Kullanarak Belirtik İşlem Uygulama
Sınıf, <xref:System.Transactions.CommittableTransaction> <xref:System.Transactions.TransactionScope> sınıfı örtülü olarak kullanmak yerine uygulamaların bir hareketi kullanması için açık bir yol sağlar. Birden çok işlevli aramalar veya birden çok iş parçacığı çağrıları arasında aynı işlemi kullanmak isteyen uygulamalar için yararlıdır. Sınıfın aksine, uygulama yazarının işlemi <xref:System.Transactions.CommittableTransaction.Commit%2A> işlemek <xref:System.Transactions.Transaction.Rollback%2A> veya iptal etmek için özellikle araması ve yöntemleri ni çağırması gerekir. <xref:System.Transactions.TransactionScope>  
  
## <a name="overview-of-the-committabletransaction-class"></a>CommittableTransaction sınıfına genel bakış  
 <xref:System.Transactions.CommittableTransaction> Sınıf türetilir <xref:System.Transactions.Transaction> sınıfı, bu nedenle tüm işlevselliğini ikincisi sağlama. Özellikle yararlıdır <xref:System.Transactions.Transaction.Rollback%2A> yöntemi <xref:System.Transactions.Transaction> geri almak için de kullanılabilir sınıf bir <xref:System.Transactions.CommittableTransaction> nesne.  
  
 <xref:System.Transactions.Transaction> Sınıf benzer <xref:System.Transactions.CommittableTransaction> sınıfının ancak teklif değil bir `Commit` yöntemi. Bu, hareketin ne zaman işlendiğini kontrol ederken işlem nesnesini (veya klonlarını) diğer yöntemlere (potansiyel olarak diğer iş parçacıklarında) geçirmenizi sağlar. Çağrılan kod kaydolabilir ve hareketi oylamak, ancak <xref:System.Transactions.CommittableTransaction> yalnızca nesnenin oluşturucusu hareketi işleme yeteneğine sahiptir.  
  
 Followings ile çalışırken dikkat etmelisiniz <xref:System.Transactions.CommittableTransaction> sınıfı  
  
- Hareket <xref:System.Transactions.CommittableTransaction> oluşturmak ortam işlemini ayarlamaz. Kaynak yöneticilerinin uygun olduğunda doğru hareket bağlamında çalışmasını sağlamak için ortam işlemini özel olarak ayarlamanız ve sıfırlamanız gerekir. Geçerli ortam işlemini ayarlamanın yolu, statik <xref:System.Transactions.Transaction.Current%2A> özelliği genel <xref:System.Transactions.Transaction> nesne üzerinde ayarlamaktır.  
  
- Bir <xref:System.Transactions.CommittableTransaction> nesne olamaz yeniden kullanılabilecek. Bir <xref:System.Transactions.CommittableTransaction> nesne bir kez işlendikten veya geri alındıktan sonra, bir harekette yeniden kullanılamaz. Diğer bir diğer adıyla, geçerli ortam hareketi bağlamı olarak ayarlanamaz.  
  
## <a name="creating-a-committabletransaction"></a>Taahhüt Edilebilir İşlem Oluşturma  
 Aşağıdaki örnek, yeni bir oluşturur <xref:System.Transactions.CommittableTransaction> ve onu kaydeder.  
  
 [!code-csharp[Tx_CommittableTx#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/tx_committabletx/cs/committabletxwithsql.cs#1)]
 [!code-vb[Tx_CommittableTx#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/tx_committabletx/vb/committabletxwithsql.vb#1)]  
  
 Bunun bir <xref:System.Transactions.CommittableTransaction> örneğini oluşturmak ortam hareketi bağlamını otomatik olarak ayarlamaz. Bu nedenle, kaynak yöneticisi üzerinde herhangi bir işlem bu hareketin bir parçası değildir. Genel <xref:System.Transactions.Transaction> <xref:System.Transactions.Transaction.Current%2A> nesneüzerindeki statik özellik ortam işlemini ayarlamak veya almak için kullanılır ve uygulama, kaynak yöneticilerinin harekete katılabileceğinden emin olmak için el ile ayarlanmalıdır. Ayrıca, <xref:System.Transactions.CommittableTransaction> nesneyi kullanmayı bitirdiğinizde eski ortam işlemini kaydetmek ve geri yüklemek de iyi bir uygulamadır.  
  
 İşlemi gerçekleştirmek için <xref:System.Transactions.CommittableTransaction.Commit%2A> yöntemi açıkça aramanız gerekir. Bir hareketi geri almak için <xref:System.Transactions.Transaction.Rollback%2A> yöntemi aramalısınız. Bir taahhüt veya geri <xref:System.Transactions.CommittableTransaction> alınana kadar, bu işlemde yer alan tüm kaynakların hala kilitli olduğunu unutmayın.  
  
 Bir <xref:System.Transactions.CommittableTransaction> işlev çağrıları ve dizileri arasında nesne kullanılabilir. Ancak, bu özel durumları işlemek ve özellikle çağırmak için uygulama geliştiricisi kadar kadar <xref:System.Transactions.Transaction.Rollback%28System.Exception%29> yöntemi hataları durumunda.  
  
## <a name="asynchronous-commit"></a>Zaman uyumsuz tamamlama  
 Sınıf, <xref:System.Transactions.CommittableTransaction> bir hareketi eşit olarak işlemek için de bir mekanizma sağlar. Birden çok veritabanı erişimi ve olası ağ gecikmesi içerebileceğiiçin, bir işlem işleme önemli ölçüde zaman alabilir. Yüksek iş gücü uygulamalarında kilitlenmeleri önlemek istediğinizde, işlem çalışmasını mümkün olan en kısa sürede bitirmek için eşsenkronize taahhüt kullanabilir ve işleme işlemini bir arka plan görevi olarak çalıştırabilirsiniz. <xref:System.Transactions.CommittableTransaction.BeginCommit%2A> Ve <xref:System.Transactions.CommittableTransaction.EndCommit%2A> yöntemlerinin <xref:System.Transactions.CommittableTransaction> sınıfı, bunu yapmak izin.  
  
 Çağırabilirsiniz <xref:System.Transactions.CommittableTransaction.BeginCommit%2A> yürütme Soyguncu iş parçacığı havuzu için bir iş parçacığı gönderme. Hareketin gerçekten <xref:System.Transactions.CommittableTransaction.EndCommit%2A> işlenmiş olup olmadığını belirlemek için de arayabilirsiniz. Hareket ne sebeple olursa olsun <xref:System.Transactions.CommittableTransaction.EndCommit%2A> işlemebaşarısız olursa, bir hareket özel durum yükseltir. Hareket çağrıldığında <xref:System.Transactions.CommittableTransaction.EndCommit%2A> henüz işlem yapılmazsa, hareket işlenene veya iptal edilene kadar arayan engellenir.  
  
 Bir zaman uyumsuz tamamlama yapmak için kolay Sistemi'ne tamamlandığında çağrılacak bir geri çağırma yöntemi sağlayarak yoludur. Ancak, çağırmalıdır <xref:System.Transactions.CommittableTransaction.EndCommit%2A> özgün yöntemini <xref:System.Transactions.CommittableTransaction> arama çağırmak için kullanılan nesne. Bu nesneyi elde etmek için, <xref:System.Transactions.CommittableTransaction> sınıf <xref:System.IAsyncResult> sınıfı uyguladığından, geri arama yönteminin *IAsyncResult* parametresini alt üst edebilirsiniz.  
  
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
- [İşlem İşlem](index.md)
