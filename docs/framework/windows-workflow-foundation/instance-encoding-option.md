---
title: Örnek kodlama seçeneği
ms.date: 03/30/2017
ms.assetid: 89e4b029-4f68-438c-8117-9b21fe094ef4
ms.openlocfilehash: cfe45428f546b6f47709c321099efdf7fbb25ef4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="instance-encoding-option"></a>Örnek kodlama seçeneği
**Örneği kodlama seçeneği** özelliği SQL iş akışı örneği deposunun SQL Kalıcılık sağlayıcısı kaydetmeden önce GZIP algoritmasını kullanarak iş akışı örneği durum bilgileri sıkıştırma olup olmadığını belirtmenize olanak sağlar Kalıcılık veritabanına bilgileri. Bu özellik için izin verilen değerler: GZip ve yok. Varsayılan değer, Yok'tur. Aşağıdaki listede, bu seçenekler açıklanmaktadır.  
  
1.  **GZip**. Kalıcılık sağlayıcı durumu bilgileri Kalıcılık veritabanında devam ettirmeden önce GZIP algoritmasını kullanarak durumu bilgilerini kodlar.  
  
2.  **Hiçbiri**. Kalıcılık sağlayıcı bilgilerin Kalıcılık veritabanına kaydedilmeden önce durum bilgilerini kodlayın değil.  
  
 İş akışı örneği durum bilgilerini kullanarak GZip kodlama SQL veritabanında bellek tüketimini azaltır ve veritabanı farklı bir bilgisayarda ağ üzerindeki iş akışı hizmeti ana bilgisayarı olduğu bilgisayardan bulunuyorsa Ayrıca ağ kullanımını azaltır çalışıyor. Genel bir yönerge ayarlamaktır **örneği kodlama seçeneği** özelliğine **hiçbiri** iş akışı örneği durum küçükse.
