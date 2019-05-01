---
title: İşlem Gerçekleştirme
ms.date: 03/30/2017
ms.assetid: effdc8e6-accf-41eb-98a5-431603ba218b
ms.openlocfilehash: dc032746b265a3e781898beb823be0d1bcf1abea
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793672"
---
# <a name="transaction-processing"></a>İşlem Gerçekleştirme
Bir çevrimiçi bir kitaplığı defterinden satın aldığınızda, bir kitap (kredi biçiminde) karşılığında exchange. Kredi iyi ise, bir dizi ilgili operations defteri alma ve kitaplığı, para alır sağlar. Ancak, tek bir işlemde serisinde exchange sırasında başarısız olursa, tüm exchange başarısız olur. Kitap alma ve kitaplığı, para almaz.  
  
 Exchange Dengeli ve tahmin edilebilir yapmaktan sorumlu teknoloji işlem çağrılır. İşlemler işlem birimi içindeki tüm işlemler başarıyla tamamlanamadığını sürece veri yönelimli kaynakları kalıcı olarak güncelleştirilmez emin olun. Tamamen başarılı ya da tamamen başarısız bir birim ilgili işlemlere kümesini birleştirerek hata kurtarma basitleştirmek ve uygulamanızı daha güvenilir hale getirebilirsiniz.  
  
 İşlem bu sistemlerin bilgisayar donanımı ve yazılımı iş yürütmek gerekli rutin işlemleri gerçekleştiren işleme dayalı bir uygulamayı barındıran oluşur. Yönetme sipariş girişi, havayolu ayırmalarını, bordro, üretim ve teslimat çalışan kayıtları, sistemleri verilebilir.  
  
 Bu bölümde, işlem hakkında genel bilgiler hem işlem uygulamalar ve Microsoft .NET Framework kullanılarak kaynak yöneticileri yazma hakkında belirli bilgi sağlar.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [İşlem Temelleri](../../../../docs/framework/data/transactions/transaction-fundamentals.md)  
 Hüküm ve kavramlarını temel işlem tanıtır.  
  
 [System.Transactions Tarafından Sağlanan Özellikler](../../../../docs/framework/data/transactions/features-provided-by-system-transactions.md)  
 Nasıl özellikleri içinde System.Transactions işlem uygulamanızı yazmak için kullanabileceğiniz anlatılmaktadır.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Transactions>  
 Kodunuzu işlemlere katılmasına izin sınıflar sağlar. Birden çok dağıtılmış katılımcıları, birden çok aşama bildirimi ve kalıcı kayıtlar ile işlemleri sınıfları destekler.
