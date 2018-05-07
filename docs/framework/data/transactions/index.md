---
title: İşlem Gerçekleştirme
ms.date: 03/30/2017
ms.assetid: effdc8e6-accf-41eb-98a5-431603ba218b
ms.openlocfilehash: dc032746b265a3e781898beb823be0d1bcf1abea
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="transaction-processing"></a>İşlem Gerçekleştirme
Bir çevrimiçi bir kitaplığı defterinden satın aldığınızda, bir kitap (kredi biçiminde) karşılığında exchange. Kredi iyi ise, bir dizi ilgili operations defteri alma ve kitaplığı, para alır sağlar. Ancak, tek bir işlemde serisinde exchange sırasında başarısız olursa, tüm exchange başarısız olur. Kitap alma ve kitaplığı, para almaz.  
  
 Exchange Dengeli ve öngörülebilir yapmaktan sorumlu teknolojisi, işlem adı verilir. İşlemler işlem birimindeki tüm işlemleri başarıyla tamamlamak sürece veri yönelimli kaynakları kalıcı olarak güncelleştirilmez emin olun. Tamamen başarılı ya da tamamen başarısız bir birim ilgili işlemlere kümesini birleştirerek hata kurtarma basitleştirmek ve uygulamanızı daha güvenilir hale getirebilirsiniz.  
  
 Hareket işleme sistemleri bilgisayar donanımı ve yazılımı iş yürütmek gerekli rutin işlemleri gerçekleştirir işleme dayalı bir uygulamayı barındıran oluşur. Örnekler yönetme sipariş girişi, uçak ayırmaları, bordro, üretim ve sevkiyat çalışan kayıtları, sistemleri içerir.  
  
 Bu bölüm hem işlem hakkında genel bilgiler ve işlemsel uygulamaları ve Microsoft .NET Framework kullanarak kaynak yöneticileri yazma konusunda belirli bilgiler sağlar.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [İşlem Temelleri](../../../../docs/framework/data/transactions/transaction-fundamentals.md)  
 Temel işlem terimleri ve kavramları işleme tanıtır.  
  
 [System.Transactions Tarafından Sağlanan Özellikler](../../../../docs/framework/data/transactions/features-provided-by-system-transactions.md)  
 Özellikleri System.Transactions işlem uygulamanızı yazmak için nasıl kullanabileceğinizi açıklar.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Transactions>  
 Kodunuzu işlemlere katılmasına izin sınıflar sağlar. Sınıfları birden fazla dağıtılmış katılımcıları, birden çok aşaması bildirimleri ve kalıcı kayıtlar ile işlemleri destekler.
