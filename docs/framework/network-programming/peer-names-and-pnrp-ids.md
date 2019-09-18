---
title: Eş Adları ve PNRP Kimlikleri
ms.date: 03/30/2017
ms.assetid: afa538e8-948f-4a98-aa9f-305134004115
ms.openlocfilehash: 15b74317507f69d2339a2e5e49b54ae72cda1a7b
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047497"
---
# <a name="peer-names-and-pnrp-ids"></a>Eş Adları ve PNRP Kimlikleri
Eş adı, bir bilgisayar, bir Kullanıcı, Grup, hizmet veya bir IPv6 adresine çözümlenebilen bir eş ile ilişkili herhangi bir şey olabilen iletişim için bir uç noktayı temsil eder. Eş adı çözümleme Protokolü (PNRP), bulut üyelerini tanımlamak için kullanılan bir PNRP KIMLIĞI oluşturmak için istatistiksel olarak benzersiz eş adı alır.  
  
## <a name="peer-names"></a>Eş adları  
 Eş adları, güvenli olmayan veya güvenli şekilde kaydedilebilir. Güvenli olmayan adlar yalnızca, kimlik sahtekarlığına tabi olan metin dizeleridir ve herkes bir yinelenen güvenli olmayan ad kaydedebilir. Güvenli olmayan adlar, özel veya korumalı ağlarda en iyi şekilde kullanılır. Güvenli adlar bir sertifikayla ve dijital imzayla korunur. Yalnızca özgün yayımcı, güvenli bir adın sahipliğini kanıtlayabilecek.  
  
 Bulut ve kapsamın birleşimi, PNRP etkinliğine katılan eşleri için makul bir güvenli ortam sağlar. Bununla birlikte, güvenli bir eş adı kullanılması Ağ uygulamasının genel güvenliğinin sağlanması gerekmez. Uygulamanın güvenliği uygulamaya bağımlıdır.  
  
 Güvenli eş adları yalnızca sahibi tarafından kaydedilir ve ortak anahtar şifrelemesi ile korunur. Güvenli bir eş adı, karşılık gelen özel anahtara sahip olan eşdüzey varlığa ait olarak değerlendirilir. Sahiplik, özel anahtar kullanılarak imzalanmış sertifikalı eş adresi (CPA) aracılığıyla etkinleştirilebilir. Kötü niyetli bir Kullanıcı, karşılık gelen özel anahtar olmadan bir eş adının sahipliğini taklit edemez.  
  
## <a name="pnrp-ids"></a>PNRP kimlikleri  
 ![pnrp kimliği](./media/fdc9e8a0-4a1c-488d-a019-bc3a1973220c.gif "fdc9e8a0-4a1c-488d-A019-bc3a1973220c")  
  
 PNRP kimlikleri aşağıdakilerden oluşur:  
  
- Eşler arası (P2P) KIMLIĞI olarak bilinen yüksek sıralı 128 bitleri, uç noktaya atanan bir eş adı karmasıdır. Eş adı şu biçimdedir: *Authority. sınıflandırıcı*. Güvenli adlar için, *yetkili* , eş adının genel anahtarının onaltılık karakterlerle GÜVENLI karma ALGORITMASı 1 (SHA1) karmasıdır. Güvenli olmayan adlar için, *yetkili* tek karakter "0" dir. *Sınıflandırıcı* , uygulamayı tanımlayan bir dizedir. Eş adı Sınıflandırıcısı, `null` Sonlandırıcı dahil 149 karakterden daha uzun olamaz.  
  
- Düşük sıralı 128 bitleri, aynı bulutta aynı P2P KIMLIĞININ farklı örneklerini tanımlayan bir üretilen sayı olan hizmet konumu için kullanılır.  
  
 P2P KIMLIĞI ve hizmet konumunun bu birleşimi, birden çok PNRP kimliğinin tek bir bilgisayardan kaydedilmesini sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Net.PeerToPeer.PeerName>
- <xref:System.Net.PeerToPeer>
