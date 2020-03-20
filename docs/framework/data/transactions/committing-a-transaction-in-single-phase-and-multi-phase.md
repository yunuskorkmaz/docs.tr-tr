---
title: Tek Aşamalı ve Çok Aşamalı İşlem Gerçekleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 694ea153-e4db-41ae-96ac-9ac66dcb69a9
ms.openlocfilehash: 8d6c51249f104d35573507a9477a24d66d770693
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174439"
---
# <a name="committing-a-transaction-in-single-phase-and-multi-phase"></a>Tek Aşamalı ve Çok Aşamalı İşlem Gerçekleştirme
Bir işlemde kullanılan her kaynak, eylemleri bir işlem yöneticisi (TM) tarafından koordine edilen bir kaynak yöneticisi (RM) tarafından yönetilir. Bir İşlem konusuna [Katılan Kaynaklar Olarak Kaydolun,](enlisting-resources-as-participants-in-a-transaction.md) bir kaynağın (veya birden çok kaynağın) bir işlemde nasıl kaydolabileceğini tartışır. Bu konu, işlem taahhüdünün kayıtlı kaynaklar arasında nasıl koordine edilebildiğini tartışır.  
  
 İşlemin sonunda, uygulama hareketin kaydedilmesini veya geri alınmasını ister. İşlem yöneticisi, bazı kaynak yöneticilerinin işlemek için oy kullanması, diğerlerinin ise hareketi geri almak için oy kullanması gibi riskleri ortadan kaldırmalıdır.  
  
 İşleminiz birden fazla kaynak içeriyorsa, iki aşamalı bir commit (2PC) gerçekleştirmeniz gerekir. İki aşamalı taahhüt protokolü (hazırlama aşaması ve işleme aşaması) işlem sona erdiğinde tüm kaynaklardaki tüm değişikliklerin tamamen kaydedilmesini veya tamamen geri atıldığında olmasını sağlar. Tüm katılımcıları sonra sonucunu bildirilir. İki aşamalı taahhüt protokolünün ayrıntılı bir tartışması için lütfen Jim Gray'in "*İşlem İşlemleme : Kavramlar ve Teknikler (Veri Yönetim Sistemlerinde Morgan Kaufmann Serisi) ISBN:1558601902*" kitabına başvurun.  
  
 Ayrıca, Tek Aşamalı İşlem protokolüne katılarak işleminizin performansını optimize edebilirsiniz. Daha fazla bilgi için, [Tek Faz Commit ve Teşvik Edilebilir Tek Faz Bildirimi kullanarak Optimizasyon'a](optimization-spc-and-promotable-spn.md)bakın.  
  
 Bir işlemin sonucu hakkında bilgi almak istiyorsanız ve oylamaya katılmak istemiyorsanız, etkinliğe <xref:System.Transactions.Transaction.TransactionCompleted> kaydolmanız gerekir.  
  
## <a name="two-phase-commit-2pc"></a>İki aşamalı kayıt (2PC)  
 İlk işlem aşamasında, hareket yöneticisi bir işlemin kaydedilmesi mi yoksa geri alınması mı gerektiğini belirlemek için her kaynağı sorgular. İkinci işlem aşamasında, işlem yöneticisi her kaynağı sorgularının sonucunu belirterek gerekli temizlemeişlemini gerçekleştirmesine olanak sağlar.  
  
 Bu tür bir işlemde yer almak için, bir kaynak yöneticisinin 2PC sırasında TM tarafından bildirim olarak adlandırılan yöntemleri sağlayan <xref:System.Transactions.IEnlistmentNotification> arabirimi uygulaması gerekir.  Aşağıdaki örnek, bu tür uygulaması örneği gösterir.  
  
 [!code-csharp[Tx_Enlist#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/tx_enlist/cs/enlist.cs#2)]
 [!code-vb[Tx_Enlist#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/tx_enlist/vb/enlist.vb#2)]  
  
### <a name="prepare-phase-phase-1"></a>Aşama (Aşama 1) hazırla  
 Uygulamadan bir <xref:System.Transactions.CommittableTransaction.Commit%2A> istek aldıktan sonra, işlem yöneticisi, her bir kaynağın işlem <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> le ilgili oylarını almak için, kayıtlı her kaynak üzerindeki yöntemi arayarak tüm kayıtlı katılımcıların Hazırlama aşamasını başlatır.  
  
 Uygular, Kaynak Yöneticisi <xref:System.Transactions.IEnlistmentNotification> arabirimi ilk uygulayan <xref:System.Transactions.IEnlistmentNotification.Prepare%28System.Transactions.PreparingEnlistment%29> yöntemi aşağıdaki basit örnekte gösterildiği gibi.  
  
```csharp
public void Prepare(PreparingEnlistment preparingEnlistment)  
{  
     Console.WriteLine("Prepare notification received");  
     //Perform work  
  
     Console.Write("reply with prepared? [Y|N] ");  
     c = Console.ReadKey();  
     Console.WriteLine();  
  
     //If work finished correctly, reply with prepared  
     if ((c.KeyChar == 'Y') || (c.KeyChar == 'y'))  
     {  
          preparingEnlistment.Prepared();  
          break;  
     }  
  
     // otherwise, do a ForceRollback  
     else if ((c.KeyChar == 'N') || (c.KeyChar == 'n'))  
     {  
          preparingEnlistment.ForceRollback();  
          break;  
     }  
}  
```  
  
 Dayanıklı kaynak yöneticisi bu çağrıyı aldığında, işlemin kurtarma bilgilerini <xref:System.Transactions.PreparingEnlistment.RecoveryInformation%2A> (özelliği alarak kullanılabilir) ve işleme işlemini tamamlamak için gereken her türlü bilgiyi kaydetmelidir. Bu içinde yapılması gerekmez <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> yöntemi olduğundan RM iş parçacığı üzerinde bunu yapabilirsiniz.  
  
 RM bittiğinde kendi iş hazırlama, yürütme veya geri çağırarak için oy <xref:System.Transactions.PreparingEnlistment.Prepared%2A> veya <xref:System.Transactions.PreparingEnlistment.ForceRollback%2A> yöntemi. Dikkat <xref:System.Transactions.PreparingEnlistment> sınıfından devralan bir <xref:System.Transactions.Enlistment.Done%2A> yönteminden <xref:System.Transactions.Enlistment> sınıfı. Bu yöntemi Hazırlama aşamasında <xref:System.Transactions.PreparingEnlistment> geri aramada ararsanız, TM'ye bunun Salt Okunur kaydı (diğer bir deyişle, işlem korumalı verileri okuyabilen ancak güncelleştiremeyen kaynak yöneticileri) olduğunu bildirir ve RM, işlem yöneticisinden 2.  
  
 Uygulama tüm kaynak yöneticileri oy <xref:System.Transactions.PreparingEnlistment.Prepared%2A>sonra işlemin başarılı bağlılık anlatılır.  
  
### <a name="commit-phase-phase-2"></a>Aşama (Aşama 2) Kaydet  
 İşlemin ikinci aşamasında, işlem yöneticisi tüm kaynak yöneticilerinden (1. aşamanın sonunda çağrılan <xref:System.Transactions.PreparingEnlistment.Prepared%2A> tüm kaynak yöneticilerinin tümünün) <xref:System.Transactions.IEnlistmentNotification.Commit%2A> başarılı prepareları alırsa, her kaynak yöneticisi için yöntemi çağırır. Kaynak yöneticileri ardından değişiklikleri kalıcı yapın ve yürütme tamamlayın.  
  
 Herhangi bir kaynak yöneticisi faz 1'de hazırlanmahatası bildirseydi, işlem yöneticisi her kaynak yöneticisi için <xref:System.Transactions.IEnlistmentNotification.Rollback%2A> yöntemi çağırır ve uygulamada commit'in başarısızlığını gösterir.  
  
 Bu nedenle, kaynak yöneticisi aşağıdaki yöntemleri uygulamanız gerekir.  
  
```csharp
public void Commit (Enlistment enlistment)  
{  
     // Do any work necessary when commit notification is received  
  
     // Declare done on the enlistment  
     enlistment.Done();  
}  
  
public void Rollback (Enlistment enlistment)  
{  
     // Do any work necessary when rollback notification is received  
  
     // Declare done on the enlistment
     enlistment.Done();
}  
```  
  
 RM, bildirim türüne göre işlemi bitirmek için gerekli her türlü çalışmayı yapmalı ve <xref:System.Transactions.Enlistment.Done%2A> <xref:System.Transactions.Enlistment> tm'ye parametredeki arama yöntemini çağırarak bitirdiğini bildirmelidir. Bu iş iş parçacığı üzerinde yapılabilir. Satır içi çağrılır aynı iş parçacığı üzerinde Aşama 2 bildirimleri oluşabilir Not <xref:System.Transactions.PreparingEnlistment.Prepared%2A> yönteminde Aşama 1. Bu nedenle, sonra herhangi bir iş yapmanız gerektiğini değil <xref:System.Transactions.PreparingEnlistment.Prepared%2A> Aşama 2 bildirimleri almadan önce tamamladınız beklediğiniz araması (örneğin, serbest bırakma kilitler).  
  
### <a name="implementing-indoubt"></a>Nin şüpheli işlemi olmadığından uygulama  
 Son olarak, uygulamalıdır <xref:System.Transactions.IEnlistmentNotification.InDoubt%2A> geçici kaynak yöneticisi için yöntem. İşlem yöneticisi bir veya daha fazla katılımcıyla iletişimi kaybederse, durumları bilinmiyorsa bu yöntem edenir. Bu durumda, işlem katılımcılarından herhangi birinin tutarsız bir durumda bırakılıp bırakılmadığını daha sonra araştırabilmeniz için bu gerçeği günlüğe kaydetmeniz gerekir.  
  
```csharp
public void InDoubt (Enlistment enlistment)  
{  
     // log this  
     enlistment.Done();  
}  
```  
  
## <a name="single-phase-commit-optimization"></a>Tek aşaması yürütme en iyi hale getirme  
 Tüm güncelleştirmeleri herhangi bir açık işbirliği yapıldığından tek aşaması yürütme Protokolü çalışma zamanında daha etkilidir. Bu protokol hakkında daha fazla bilgi için, [Tek Faz Commit ve Teşvik Edilebilir Tek Faz Bildirimi kullanarak Optimizasyon'a](optimization-spc-and-promotable-spn.md)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tek Aşamalı İşleme ve Yükseltilebilir Tek Aşamalı Bildirim kullanarak en iyi duruma getirme](optimization-spc-and-promotable-spn.md)
- [Bir İşlemde Kaynakları Katılımcı Olarak Kaydetme](enlisting-resources-as-participants-in-a-transaction.md)
