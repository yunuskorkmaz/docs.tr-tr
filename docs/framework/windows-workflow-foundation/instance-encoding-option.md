---
title: Örnek Kodlama Seçeneği
ms.date: 03/30/2017
ms.assetid: 89e4b029-4f68-438c-8117-9b21fe094ef4
ms.openlocfilehash: c4de7c45d899f45a7b5b71d563257d9accb8fdbb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61928730"
---
# <a name="instance-encoding-option"></a>Örnek Kodlama Seçeneği
**Örnek kodlama seçeneği** SQL iş akışı örneği Store özelliğini SQL kalıcı bir sağlayıcı kaydetmeden önce GZip algoritmasıyla iş akışı örneği durumu bilgileri sıkıştırma belirtmenize olanak sağlar Kalıcılık veritabanı bilgileri. Bu özellik için izin verilen değerler şunlardır: GZip ve yok. Varsayılan değer, Yok'tur. Aşağıdaki listede, bu seçenekler açıklanmaktadır.  
  
1. **GZip**. Kalıcılık veritabanı durumu bilgileri devam ettirmeden önce GZip algoritmasıyla durum bilgilerini kalıcı bir sağlayıcı kodlar.  
  
2. **Hiçbiri**. Kalıcı bir sağlayıcı bilgileri Kalıcılık veritabanına kaydedilmeden önce durum bilgilerini kodlamaz.  
  
 İş akışı örneği durumu bilgileri kullanarak GZip kodlama SQL veritabanında bellek tüketimini azaltır ve iş akışı hizmeti konağı olduğu bir bilgisayardan farklı bir bilgisayara ağ üzerinde veritabanının bulunduğu, ayrıca ağ kullanımını azaltır çalışıyor. Genel bir kılavuz ayarlamaktır **örnek kodlama seçeneği** özelliğini **hiçbiri** iş akışı örneği durumu küçükse.
