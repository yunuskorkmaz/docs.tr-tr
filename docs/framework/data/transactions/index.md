---
title: İşlem Gerçekleştirme
description: .NET 'te işlem işlemeyi gözden geçirin. İşlemler, tüm işlemler başarıyla tamamlanmadığı takdirde veri odaklı kaynakların kalıcı olarak güncelleştirilmesini sağlamaktır.
ms.date: 03/30/2017
ms.assetid: effdc8e6-accf-41eb-98a5-431603ba218b
ms.openlocfilehash: 30d69c55d968865cc80b8633bdbc2442f6d216de
ms.sourcegitcommit: 6219b1e1feccb16d88656444210fed3297f5611e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/22/2020
ms.locfileid: "85141919"
---
# <a name="transaction-processing"></a>İşlem Gerçekleştirme
Bir çevrimiçi bir kitaplığı defterinden satın aldığınızda, bir kitap (kredi biçiminde) karşılığında exchange. Kredi iyi ise, bir dizi ilgili operations defteri alma ve kitaplığı, para alır sağlar. Ancak, tek bir işlemde serisinde exchange sırasında başarısız olursa, tüm exchange başarısız olur. Kitap alma ve kitaplığı, para almaz.  
  
 Exchange dengeli ve öngörülebilir hale getirmekten sorumlu teknoloji işlem işleme olarak adlandırılır. İşlemler, işlem birimi içindeki tüm işlemler başarıyla tamamlanmadığı takdirde veri odaklı kaynakların kalıcı olarak güncelleştirilmesini sağlamaktır. Tamamen başarılı ya da tamamen başarısız bir birim ilgili işlemlere kümesini birleştirerek hata kurtarma basitleştirmek ve uygulamanızı daha güvenilir hale getirebilirsiniz.  
  
 İşlem işleme sistemleri, iş yürütmek için gereken rutin işlemleri gerçekleştiren bir işlem odaklı uygulamayı barındıran bilgisayar donanımlarından ve yazılımından oluşur. Örnek olarak, satış siparişi girişi, hava yolu ayırmaları, bordro, çalışan kayıtları, üretim ve Sevkiyat yönetimi gibi sistemler bulunur.  
  
 Bu bölüm, işlem işleme hakkında genel bilgi ve Microsoft .NET çerçevesini kullanarak işlem uygulamalarının ve kaynak yöneticilerinin nasıl yazılacağı hakkında belirli bilgiler sağlar.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [İşlem Temelleri](transaction-fundamentals.md)  
 Temel işlem işleme hüküm ve kavramlarını tanıtır.  
  
 [System.Transactions Tarafından Sağlanan Özellikler](features-provided-by-system-transactions.md)  
 Kendi işlem uygulamanızı yazmak için System. Transactions içindeki özellikleri nasıl kullanabileceğinizi açıklar.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Transactions>  
 Kodunuzun işlemlere katılmasına izin veren sınıflar sağlar. Sınıflar birden çok dağıtılmış katılımcı, birden çok aşama bildirimi ve kalıcı kayıtlar içeren işlemleri destekler.
