---
description: 'Daha fazla bilgi edinin: eş adları ve PNRP kimlikleri'
title: Eş Adları ve PNRP Kimlikleri
ms.date: 03/30/2017
ms.assetid: afa538e8-948f-4a98-aa9f-305134004115
ms.openlocfilehash: ff9f77917ef05754f2373369d623b66e66b5a753
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801871"
---
# <a name="peer-names-and-pnrp-ids"></a>Eş Adları ve PNRP Kimlikleri

Eş adı, bir bilgisayar, bir Kullanıcı, Grup, hizmet veya bir IPv6 adresine çözümlenebilen bir eş ile ilişkili herhangi bir şey olabilen iletişim için bir uç noktayı temsil eder. Eş adı çözümleme Protokolü (PNRP), bulut üyelerini tanımlamak için kullanılan bir PNRP KIMLIĞI oluşturmak için istatistiksel olarak benzersiz eş adı alır.  
  
## <a name="peer-names"></a>Eş adları  

 Eş adları, güvenli olmayan veya güvenli şekilde kaydedilebilir. Güvenli olmayan adlar yalnızca, kimlik sahtekarlığına tabi olan metin dizeleridir ve herkes bir yinelenen güvenli olmayan ad kaydedebilir. Güvenli olmayan adlar, özel veya korumalı ağlarda en iyi şekilde kullanılır. Güvenli adlar bir sertifikayla ve dijital imzayla korunur. Yalnızca özgün yayımcı, güvenli bir adın sahipliğini kanıtlayabilecek.  
  
 Bulut ve kapsamın birleşimi, PNRP etkinliğine katılan eşleri için makul bir güvenli ortam sağlar. Bununla birlikte, güvenli bir eş adı kullanılması Ağ uygulamasının genel güvenliğinin sağlanması gerekmez. Uygulamanın güvenliği uygulamaya bağımlıdır.  
  
 Güvenli eş adları yalnızca sahibi tarafından kaydedilir ve ortak anahtar şifrelemesi ile korunur. Güvenli bir eş adı, karşılık gelen özel anahtara sahip olan eşdüzey varlığa ait olarak değerlendirilir. Sahiplik, özel anahtar kullanılarak imzalanmış sertifikalı eş adresi (CPA) aracılığıyla etkinleştirilebilir. Kötü niyetli bir Kullanıcı, karşılık gelen özel anahtar olmadan bir eş adının sahipliğini taklit edemez.  
  
## <a name="pnrp-ids"></a>PNRP kimlikleri  

 ![PNRP KIMLIĞI](./media/fdc9e8a0-4a1c-488d-a019-bc3a1973220c.gif "fdc9e8a0-4a1c-488d-a019-bc3a1973220c")  
  
 PNRP kimlikleri aşağıdakilerden oluşur:  
  
- Eşler arası (P2P) KIMLIĞI olarak bilinen yüksek sıralı 128 bitleri, uç noktaya atanan bir eş adı karmasıdır. Eş adı şu biçimdedir: *Authority. sınıflandırıcı*. Güvenli adlar için, *yetkili* , eş adının genel anahtarının onaltılık karakterlerle GÜVENLI karma ALGORITMASı 1 (SHA1) karmasıdır. Güvenli olmayan adlar için, *yetkili* tek karakter "0" dir. *Sınıflandırıcı* , uygulamayı tanımlayan bir dizedir. Eş adı Sınıflandırıcısı, Sonlandırıcı dahil 149 karakterden daha uzun olamaz `null` .  
  
- Düşük sıralı 128 bitleri, aynı bulutta aynı P2P KIMLIĞININ farklı örneklerini tanımlayan bir üretilen sayı olan hizmet konumu için kullanılır.  
  
 P2P KIMLIĞI ve hizmet konumunun bu birleşimi, birden çok PNRP kimliğinin tek bir bilgisayardan kaydedilmesini sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Net.PeerToPeer.PeerName>
- <xref:System.Net.PeerToPeer>
