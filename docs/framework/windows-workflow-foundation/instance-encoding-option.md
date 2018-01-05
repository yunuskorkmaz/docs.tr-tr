---
title: "Örnek kodlama seçeneği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 89e4b029-4f68-438c-8117-9b21fe094ef4
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a7664eecb68ff9aec0f5e3e31aa08058700f0e92
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="instance-encoding-option"></a>Örnek kodlama seçeneği
**Örneği kodlama seçeneği** özelliği SQL iş akışı örneği deposunun SQL Kalıcılık sağlayıcısı kaydetmeden önce GZIP algoritmasını kullanarak iş akışı örneği durum bilgileri sıkıştırma olup olmadığını belirtmenize olanak sağlar Kalıcılık veritabanına bilgileri. Bu özellik için izin verilen değerler: GZip ve yok. Varsayılan değer, Yok'tur. Aşağıdaki listede, bu seçenekler açıklanmaktadır.  
  
1.  **GZip**. Kalıcılık sağlayıcı durumu bilgileri Kalıcılık veritabanında devam ettirmeden önce GZIP algoritmasını kullanarak durumu bilgilerini kodlar.  
  
2.  **Hiçbiri**. Kalıcılık sağlayıcı bilgilerin Kalıcılık veritabanına kaydedilmeden önce durum bilgilerini kodlayın değil.  
  
 İş akışı örneği durum bilgilerini kullanarak GZip kodlama SQL veritabanında bellek tüketimini azaltır ve veritabanı farklı bir bilgisayarda ağ üzerindeki iş akışı hizmeti ana bilgisayarı olduğu bilgisayardan bulunuyorsa Ayrıca ağ kullanımını azaltır çalışıyor. Genel bir yönerge ayarlamaktır **örneği kodlama seçeneği** özelliğine **hiçbiri** iş akışı örneği durum küçükse.
