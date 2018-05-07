---
title: 'İşlem özelleştirme: genel bakış'
ms.date: 03/30/2017
ms.assetid: a3546296-1443-4b88-aa6e-d41011041ba7
ms.openlocfilehash: d495632faf2f57df21d07e0be85244d7ba9d9da7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="customizing-operations-overview"></a>İşlem özelleştirme: genel bakış
Varsayılan olarak, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dinamik SQL ekleme, güncelleştirme ve silme işlemleri eşlemesini göre oluşturur. Bununla birlikte, pratikte genellikle güvenlik, doğrulama ve benzeri için sağlamak için kendi iş mantığı eklemek istediğiniz.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Bu işlemler özelleştirme teknikler arasında şunlar yer alır.  
  
## <a name="loading-options"></a>Yükleme Seçenekleri  
 Sorgularınızda, veritabanına bağlandığında ana hedefiniz ilgili ne kadar veri alındığını kontrol edebilirsiniz. Bu işlev büyük ölçüde kullanılarak uygulanır <xref:System.Data.Linq.DataLoadOptions>. Daha fazla bilgi için bkz: [hemen yüklenirken karşı ertelenmiş](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).  
  
## <a name="partial-methods"></a>Kısmi Yöntemler  
 Kendi varsayılan eşlemesinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , iş mantığı uygulamanıza yardımcı olmak için kısmi yöntemler sağlar. Daha fazla bilgi için bkz: [ekleme iş mantığı tarafından kısmi yöntemlerini kullanarak](../../../../../../docs/framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md).  
  
## <a name="stored-procedures-and-user-defined-functions"></a>Saklı yordamlar ve kullanıcı tanımlı işlevler  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] saklı yordamlar ve kullanıcı tanımlı işlevler kullanımını destekler. Saklı yordamlar operations özelleştirmek için sık kullanılır. Daha fazla bilgi için bkz: [saklı yordamlar](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Insert, Update ve Delete İşlemlerini Özelleştirme](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
