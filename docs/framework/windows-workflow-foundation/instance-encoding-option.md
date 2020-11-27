---
title: Örnek Kodlama Seçeneği
ms.date: 03/30/2017
ms.assetid: 89e4b029-4f68-438c-8117-9b21fe094ef4
ms.openlocfilehash: 416394eb346a7c82385da32a89bd54179b255cd4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96279902"
---
# <a name="instance-encoding-option"></a>Örnek Kodlama Seçeneği

SQL Iş akışı örneği deposunun **örnek kodlama seçeneği** ÖZELLIĞI, SQL kalıcılık sağlayıcısı 'nın, bilgileri kalıcılık veritabanına kaydetmeden önce gzip algoritmasını kullanarak iş akışı örneği durum bilgilerini sıkıştırmak gerekip gerekmediğini belirtmenizi sağlar. Bu özellik için izin verilen değerler: GZip ve None. Varsayılan değer, Yok'tur. Aşağıdaki listede bu seçenekler açıklanmaktadır.  
  
1. **Gzip**. Kalıcılık sağlayıcısı, kalıcılık veritabanındaki durum bilgilerini kalıcı yapmadan önce GZip algoritmasını kullanarak durum bilgilerini kodlar.  
  
2. **Yok**. Kalıcılık sağlayıcısı, bilgileri kalıcılık veritabanına kaydetmeden önce durum bilgilerini kodlamaz.  
  
 GZip kullanan iş akışı örneği durum bilgileri, SQL veritabanında bellek tüketimini azaltır ve ayrıca veritabanı, iş akışı hizmeti konağının çalıştığı bilgisayardan ağdaki farklı bir bilgisayarda bulunuyorsa ağ tüketimini azaltır. Genel bir kılavuz, iş akışı örneği durumu küçükse **örnek kodlama seçeneği** özelliğini **none** olarak ayarlamanıza yardımcı olur.
