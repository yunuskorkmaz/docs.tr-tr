---
title: Eş Adları ve PNRP Kimlikleri
ms.date: 03/30/2017
ms.assetid: afa538e8-948f-4a98-aa9f-305134004115
ms.openlocfilehash: 15b74317507f69d2339a2e5e49b54ae72cda1a7b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047497"
---
# <a name="peer-names-and-pnrp-ids"></a>Eş Adları ve PNRP Kimlikleri
Eş Adı, bilgisayar, kullanıcı, grup, hizmet veya Bir Eşle ilişkili ve IPv6 adresine çözülebilen herhangi bir iletişim bitiş noktasını temsil eder. Eş Adı Çözümleme Protokolü (PNRP), bulut üyelerini tanımlamak için kullanılan bir PNRP kimliği oluşturulması için istatistiksel olarak benzersiz Eş Adı alır.  
  
## <a name="peer-names"></a>Eş Adları  
 Eş adları güvenli olmayan veya güvenli olarak kaydedilebilir. Güvenli olmayan adlar, kopyalanmış güvenli olmayan bir adı kaydedebileceğinden, yalnızca sahtesine tabi olan metin dizeleridir. Güvenli olmayan adlar en iyi özel veya başka korumalı ağlarda kullanılır. Güvenli adlar sertifika ve dijital imza ile korunur. Yalnızca özgün yayımcı, güvenli bir adın sahipliğini kanıtlayabilir.  
  
 Bulut ve kapsam birleşimi, PNRP etkinliğine katılan eşler için oldukça güvenli bir ortam sağlar. Ancak, güvenli bir eş adı kullanmak ağ uygulamasının genel güvenliğini sağlamaz. Uygulamanın güvenliği uygulamaya bağlıdır.  
  
 Güvenli eş adları yalnızca sahibi tarafından kaydedilir ve ortak anahtar şifrelemesi ile korunur. Güvenli bir eş adı, ilgili özel anahtara sahip eş tüzel kişi tarafından sahip olunan kabul edilir. Mülkiyet, özel anahtar kullanılarak imzalanan onaylı eş adresi (CpA) ile kanıtlanabilir. Kötü niyetli bir kullanıcı, karşılık gelen özel anahtar olmadan bir eş adının sahipliğini taklit edemez.  
  
## <a name="pnrp-ids"></a>PNRP Tİp'leri  
 ![PNRP Kimliği](./media/fdc9e8a0-4a1c-488d-a019-bc3a1973220c.gif "fdc9e8a0-4a1c-488d-a019-bc3a1973220c")  
  
 PNRP T'leri aşağıdakilerden oluşur:  
  
- Eşler arası (P2P) kimliği olarak bilinen yüksek sıralı 128 bit, bitiş noktasına atanan bir eş adının karmasIdır. Eş adı aşağıdaki biçimi vardır: *Authority.Classifier*. Güvenli adlar için *Otorite,* altıgen karakterdeki eş adının ortak anahtarının Güvenli Karma Algoritma 1 (SHA1) karmasıdır. Güvenli olmayan adlar için *Otorite* tek karakter "0"dır. *Sınıflandırıcı,* uygulamayı tanımlayan bir dizedir. Hiçbir eş adı sınıflandırıcı, `null` sonlandırıcı da dahil olmak üzere 149 karakterden uzun olamaz.  
  
- Düşük sıralı 128 bit, aynı buluttaki aynı P2P KIMLIĞI'nin farklı örneklerini tanımlayan oluşturulan bir sayı olan Hizmet Konumu için kullanılır.  
  
 P2P Kimliği ve Hizmet Konumu'nun bu birleşimi, birden çok PNRP kimliğinin tek bir bilgisayardan kaydedilmesine olanak tanır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Net.PeerToPeer.PeerName>
- <xref:System.Net.PeerToPeer>
