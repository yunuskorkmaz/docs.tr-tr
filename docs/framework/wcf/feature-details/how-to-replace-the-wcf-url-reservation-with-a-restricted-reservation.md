---
title: 'Nasıl yapılır: WCF URL Ayırmayı Kısıtlı Ayırma ile Değiştirme'
ms.date: 03/30/2017
ms.assetid: 2754d223-79fc-4e2b-a6ce-989889f2abfa
ms.openlocfilehash: b53596d7ac4e7e7c3748f6a98130492a96c0b48c
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45610041"
---
# <a name="how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation"></a>Nasıl yapılır: WCF URL Ayırmayı Kısıtlı Ayırma ile Değiştirme
Bir URL ayırmasını kullanan bir URL veya URL bir dizi ileti alabilir sınırlamak sağlar. Ayırma, bir URL şablonu, erişim denetimi listesi (ACL) ve bir dizi bayrakları oluşur. URL şablonu ayırma etkiler hangi URL'leri tanımlar. URL şablonları nasıl işlendiği hakkında daha fazla bilgi için bkz. [yönlendirme gelen istekleri](https://go.microsoft.com/fwlink/?LinkId=136764). Belirtilen URL'lerden iletileri almak için hangi kullanıcı veya kullanıcı grubuna izin ACL denetler. Bayrakları ayırma URL'yi doğrudan dinleyecek şekilde veya başka bir işlem için dinlemek için temsilci izni verme için bir kullanıcı veya gruba izin vermek için uygun olup olmadığını gösterir.  
  
 Varsayılan işletim sistemi yapılandırmasının bir parçası olarak, Windows Communication Foundation (WCF) çift yönlü iletişim için çift bir HTTP bağlaması kullanan uygulamaları çalıştırmak tüm kullanıcılar'ı etkinleştirmek için 80 numaralı bağlantı noktası için genel olarak erişilebilir bir ayırma oluşturur. Bu rezervasyon ACL herkes için olduğundan, yöneticileri izin açıkça olamaz veya bir URL veya URL kümesi üzerinde dinleme izni izin vermeyin. Bu konu, silme bu ayırma ve ayırmayı kısıtlı bir ACL ile yeniden oluşturma işlemini açıklar.  
  
 Üzerinde [!INCLUDE[wv](../../../../includes/wv-md.md)] veya [!INCLUDE[lserver](../../../../includes/lserver-md.md)] yazarak tüm HTTP URL ayırmaları yükseltilmiş bir komut isteminden görüntüleyebilirsiniz `netsh http show urlacl`.  Aşağıdaki örnek, bir WCF URL ayırmayı benzer olmalıdır gösterir.  
  
```  
Reserved URL : http://+:80/Temporary_Listen_Addresses/  
        User: \Everyone  
            Listen: Yes  
            Delegate: No  
            SDDL: D:(A;;GX;;;WD)  
```  
  
 WCF uygulaması çift yönlü iletişim için HTTP çift bağlama kullanırken bir URL şablonu ayırma oluşur. Bu formu URL'leri bir WCF hizmeti için bir HTTP çift bağlama üzerinden iletişim kurarken WCF istemciye iletileri geri göndermek için kullanılır. Herkes, başka bir işleme barındırılmaya değil ancak URL üzerinde dinlemek için izin verilir. Son olarak, ACL Güvenlik Tanımlayıcısı Tanım Dili (SSDL) açıklanmıştır. SSDL hakkında daha fazla bilgi için bkz: [SSDL](https://go.microsoft.com/fwlink/?LinkId=136789)  
  
### <a name="to-delete-the-wcf-url-reservation"></a>WCF URL ayırmayı silmek için  
  
1.  Tıklayın **Başlat**, işaret **tüm programlar**, tıklayın **Donatılar**, sağ **komut istemi** tıklatıp **farklı çalıştır Yönetici** bağlam menüsünde gelir. Tıklayın **devam** kullanıcı hesabı denetimi (UAC) penceresinde, devam etmek için izinler isteyebilir.  
  
2.  Yazın **netsh http delete urlacl url =http://+:80/Temporary_Listen_Addresses/**  komut istemi penceresinde.  
  
3.  Rezervasyon başarıyla silinirse, aşağıdaki ileti görüntülenir. **URL ayırmasını başarıyla silindi**  
  
## <a name="creating-a-new-security-group-and-new-restricted-url-reservation"></a>Yeni güvenlik grubu ve yeni kısıtlı URL ayırmasını oluşturma  
 WCF URL ayırmayı kısıtlı ayırma ile değiştirme için öncelikle yeni bir güvenlik grubu oluşturmanız gerekir. Bunu iki yoldan biriyle yapabilirsiniz: komut isteminden veya bilgisayar Yönetim Konsolu'ndan. Yalnızca birini yapmanız gerekir.  
  
#### <a name="to-create-a-new-security-group-from-a-command-prompt"></a>Bir komut istemi'nden yeni bir güvenlik grubu oluşturmak için  
  
1.  Tıklayın **Başlat**, işaret **tüm programlar**, tıklayın **Donatılar**, sağ **komut istemi** tıklatıp **farklı çalıştır Yönetici** bağlam menüsünde gelir. Tıklayın **devam** kullanıcı hesabı denetimi (UAC) penceresinde, devam etmek için izinler isteyebilir.  
  
2.  Yazın **net localgroup "\<güvenlik grubu adı >" / Açıklama: "\<güvenlik grubu açıklaması >" / add** komut isteminde. Değiştirme  **\<güvenlik grubu adı >** oluşturmak istediğiniz güvenlik grubunun adıyla ve  **\<güvenlik grubu açıklaması >** için uygun bir açıklama ile güvenlik grubu.  
  
3.  Güvenlik grubu başarıyla oluşturulursa, aşağıdaki ileti görüntülenir. **Komutu başarıyla tamamlandı.**  
  
#### <a name="to-create-a-new-security-group-from-the-computer-management-console"></a>Bilgisayar yönetim konsolundan yeni bir güvenlik grubu oluşturmak için  
  
1.  Tıklayın **Başlat**, tıklayın **Denetim Masası**, tıklayın **Yönetimsel Araçlar**, tıklatıp **Bilgisayar Yönetimi** bilgisayarı açmak için Yönetim Konsolu. Tıklayın **devam** kullanıcı hesabı denetimi (UAC) penceresinde, devam etmek için izinler isteyebilir.  
  
2.  Tıklayın **Sistem Araçları**, tıklayın **yerel kullanıcılar ve gruplar**, sağ **grupları** klasörü ve tıklatın **yeni grup** bağlam menüsünde, gelir. İstenen türü **grup adı**, **açıklama** ve diğer ayrıntıları bu yeni güvenlik grubu ve tıklatın **Oluştur** güvenlik grubu oluşturmak için düğme.  
  
#### <a name="to-create-the-restricted-url-reservation"></a>Kısıtlı URL ayırması oluşturmak için  
  
1.  Tıklayın **Başlat**, işaret **tüm programlar**, tıklayın **Donatılar**, sağ **komut istemi** tıklatıp **farklı çalıştır Yönetici** bağlam menüsünde gelir. Tıklayın **devam** kullanıcı hesabı denetimi (UAC) penceresinde, devam etmek için izinler isteyebilir.  
  
2.  Yazın **netsh http ekleme urlacl url =http://+:80/Temporary_Listen_Addresses/ kullanıcı = "\<makine adı >\\< güvenlik grubu adı\>**  komut isteminde. Değiştirme  **\<makine adı >** grubu oluşturulmalıdır bilgisayar adını ve  **\<güvenlik grubu adı >** oluşturduğunuz güvenlik grubunun adıyla daha önce.  
  
3.  Rezervasyon başarıyla oluşturulursa, aşağıdaki ileti görüntülenir. **URL ayırmasını başarıyla eklendi**.
