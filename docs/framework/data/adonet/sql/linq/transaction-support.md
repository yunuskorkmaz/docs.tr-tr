---
title: İşlem Desteği
ms.date: 03/30/2017
ms.assetid: 8cceb26e-8d36-4365-8967-58e2e89e0187
ms.openlocfilehash: 9c7128ef432fa609b8d628bc74caebe790058ede
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792282"
---
# <a name="transaction-support"></a>İşlem Desteği
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]üç ayrı işlem modelini destekler. Aşağıda, bu modeller gerçekleştirilen denetim sırasına göre listelenmiştir.  
  
## <a name="explicit-local-transaction"></a>Açık Yerel Işlem  
 Çağrıldığında, <xref:System.Data.Linq.DataContext.Transaction%2A> özelliği bir`IDbTransaction` ()işlemiolarakayarlandıysa,çağrıaynıişlembağlamındayürütülür.<xref:System.Data.Linq.DataContext.SubmitChanges%2A> <xref:System.Data.Linq.DataContext.SubmitChanges%2A>  
  
 İşlemin başarılı bir şekilde yürütülmesinden sonra işlemi yürütme veya geri alma sorumluluğu sizin sorumluluğunuzdadır. İşleme karşılık gelen bağlantı, <xref:System.Data.Linq.DataContext>oluşturmak için kullanılan bağlantıyla aynı olmalıdır. Farklı bir bağlantı kullanılıyorsa bir özel durum oluşturulur.  
  
## <a name="explicit-distributable-transaction"></a>Açık dağıtılabilir Işlem  
 Etkin <xref:System.Data.Linq.DataContext.SubmitChanges%2A> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bir<xref:System.Transactions.Transaction>kapsamda API 'leri (bunlarla sınırlı olmamak üzere) çağırabilirsiniz. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]çağrının bir işlemin kapsamında olduğunu ve yeni bir işlem oluşturmediğini algılar. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Ayrıca, bu durumda bağlantının kapatılması önlenir. Bu tür bir işlemin bağlamında <xref:System.Data.Linq.DataContext.SubmitChanges%2A> sorgu ve yürütmeler gerçekleştirebilirsiniz.  
  
## <a name="implicit-transaction"></a>Örtük Işlem  
 ' İ çağırdığınızda <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] çağrının bir <xref:System.Transactions.Transaction> veya `Transaction` özelliğinin kapsamında olup olmadığını denetler (`IDbTransaction`), Kullanıcı tarafından başlatılan bir yerel işlem olarak ayarlanır. Hiç bir işlem bulmazsa, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] yerel bir işlem (`IDbTransaction`) başlatır ve oluşturulan SQL komutlarını yürütmek için onu kullanır. Tüm SQL komutları başarıyla tamamlandığında, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] yerel işlemi kaydeder ve döndürür.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Arka Plan Bilgileri](background-information.md)
- [Nasıl yapılır: Işlemleri kullanarak köşeli ayraç veri gönderimleri](how-to-bracket-data-submissions-by-using-transactions.md)
