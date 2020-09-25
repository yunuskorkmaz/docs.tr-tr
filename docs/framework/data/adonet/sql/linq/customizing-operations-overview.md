---
title: 'İşlemleri Özelleştirme: Genel Bakış'
ms.date: 03/30/2017
ms.assetid: a3546296-1443-4b88-aa6e-d41011041ba7
ms.openlocfilehash: d4d375716e3199afcbbb9bbd8b8b04867ca0e5fa
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173529"
---
# <a name="customizing-operations-overview"></a>İşlemleri Özelleştirme: Genel Bakış

Varsayılan olarak, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] eşlemeye göre INSERT, Update ve DELETE işlemleri için dınamık SQL oluşturur. Bununla birlikte, pratikte güvenlik, doğrulama ve benzerlerini sağlamak üzere kendi iş mantığınızı eklemek istersiniz.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Bu işlemleri özelleştirmeye yönelik teknikler şunlardır.  
  
## <a name="loading-options"></a>Yükleme seçenekleri  

 Sorgularda, veritabanına bağlandığınızda ana Hedefinizdeki ilgili verilerin ne kadarının alındığını denetleyebilirsiniz. Bu işlevsellik büyük ölçüde kullanılarak uygulanır <xref:System.Data.Linq.DataLoadOptions> . Daha fazla bilgi için bkz. [ertelenmiş ve hemen yükleme](deferred-versus-immediate-loading.md).  
  
## <a name="partial-methods"></a>Kısmi Yöntemler  

 Varsayılan eşlemesinde, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] iş mantığınızı uygulamanıza yardımcı olacak kısmi yöntemler sağlar. Daha fazla bilgi için bkz. [kısmi yöntemler kullanarak Iş mantığı ekleme](adding-business-logic-by-using-partial-methods.md).  
  
## <a name="stored-procedures-and-user-defined-functions"></a>Saklı yordamlar ve Kullanıcı tanımlı Işlevler  

 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , saklı yordamların ve Kullanıcı tanımlı işlevlerin kullanımını destekler. Saklı yordamlar, işlemleri özelleştirmek için sık sık kullanılır. Daha fazla bilgi için bkz. [saklı yordamlar](stored-procedures.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Insert, Update ve Delete İşlemlerini Özelleştirme](customizing-insert-update-and-delete-operations.md)
