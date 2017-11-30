---
title: "Eş adlarını ve PNRP kimlikleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: afa538e8-948f-4a98-aa9f-305134004115
caps.latest.revision: "5"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: c5b4bcf0a7a7d23dd54fad36b341e3ed241975b3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="peer-names-and-pnrp-ids"></a>Eş adlarını ve PNRP kimlikleri
Eş adı bir bilgisayar, bir kullanıcı, bir grup, bir hizmet veya bir IPv6 adresine çözülebilir bir eş ile ilişkili herhangi bir şey olabilir, iletişimi için bir uç noktasını temsil eder. Eş Adı Çözümleme Protokolü (PNRP) bir PNRP bulut üyelerini tanımlamak için kullanılan kimliği oluşturulması için istatistiksel olarak benzersiz eş adını alır.  
  
## <a name="peer-names"></a>Eş adları  
 Eş adları olarak kaydedilebilir güvenli veya güvenli. Herhangi bir yinelenen güvenli olmayan ad kaydedebilecekleri güvenli yalnızca yanıltma tabi olan metin dizelerini adlardır. Güvenli olmayan adlar en iyi özel veya aksi korumalı ağlarda kullanılır. Güvenli adları bir sertifika ve dijital imza ile korunur. Yalnızca özgün yayımcısı güvenli bir ad sahipliğini kanıtlamak mümkün olacaktır.  
  
 Bulut ve kapsamın birleşimi PNRP etkinliğinde katılmak eşleri için makul biçimde güvenli bir ortam sağlar. Ancak, bir güvenli Eş adı kullanarak Ağ uygulamasının genel güvenlik olunmasını sağlamamasıdır. Güvenlik uygulamasının uygulama bağımlıdır.  
  
 Güvenli eş adları, yalnızca kendi sahibi tarafından kaydedilir ve ortak anahtar şifrelemesi ile korunan. Güvenli eş adını ilgili özel anahtara sahip eş varlık tarafından ait kabul edilir. Sahipliği özel anahtarı ile imzalanmış sertifikalı eş adresi (CPA) oluyor uygulamasına yol açıyordu. Kötü niyetli bir kullanıcının bir eş adı karşılık gelen özel anahtar olmadan sahipliğini taklit edilemez.  
  
## <a name="pnrp-ids"></a>PNRP kimlikleri  
 ![PNRP kimliği](../../../docs/framework/network-programming/media/fdc9e8a0-4a1c-488d-a019-bc3a1973220c.gif "fdc9e8a0-4a1c-488d-a019-bc3a1973220c")  
  
 PNRP kimlikleri aşağıdakilerden oluşur:  
  
-   Yüksek düzey 128 bit eşler arası (P2P) kimliği olarak da bilinen eş adı uç noktasına atanmış karmasını değerleridir. Eş adı şu biçimdedir: *Authority.Classifier*. Güvenli adları için *yetkilisi* onaltılı karakter Eş adı ortak anahtarını Güvenli Karma Algoritması 1 (SHA1) karmasıdır. Güvenli olmayan adları için *yetkilisi* "0" joker karakterleri desteklenir. *Sınıflandırıcı* uygulama tanımlayan bir dize değil. Hiçbir eş adı sınıflandırıcı 149 karakterden uzun dahil olmak üzere büyük `null` Sonlandırıcı.  
  
-   Düşük düzey 128 bit aynı P2P kimliği aynı buluttaki farklı örneklerini tanımlayan oluşturulan bir sayıdır hizmet konumu için kullanılır.  
  
 Bu birleşim P2P Kimliğinin ve hizmet konumu tek bir bilgisayardan kaydedilmesi birden çok PNRP kimlikleri sağlar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Net.PeerToPeer.PeerName>  
 <xref:System.Net.PeerToPeer>
