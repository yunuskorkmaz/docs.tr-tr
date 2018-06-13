---
title: 'Nasıl yapılır: WCF URL Ayırmayı Kısıtlı Ayırma ile Değiştirme'
ms.date: 03/30/2017
ms.assetid: 2754d223-79fc-4e2b-a6ce-989889f2abfa
ms.openlocfilehash: 823a59f53823a2480655c4f8720504dd4199d0bc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33495284"
---
# <a name="how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation"></a>Nasıl yapılır: WCF URL Ayırmayı Kısıtlı Ayırma ile Değiştirme
Bir URL ayırmasını URL'yi veya URL'leri kümesini kimin ileti alabilir kısıtlamak sağlar. Bir ayırma bir URL şablonu, bir erişim denetimi listesi (ACL) ve bir dizi bayrakları oluşur. URL şablonu ayırma etkiler hangi URL'leri tanımlar. URL şablonları nasıl işlendiği hakkında daha fazla bilgi için bkz: [yönlendirme gelen istekleri](http://go.microsoft.com/fwlink/?LinkId=136764). Belirtilen URL'lerden iletileri almak için hangi kullanıcı veya kullanıcı grubuna izin ACL denetler. Bayrakları ayırma URL üzerinde doğrudan dinlemek veya başka bir işlem dinlemek için temsilci izni verme için bir kullanıcı veya grup izin vermek için olup olmadığını belirtin.  
  
 Varsayılan işletim sistemi yapılandırmasının bir parçası olarak, Windows Communication Foundation (WCF) çift yönlü iletişim için çift HTTP bağlama kullanan uygulamaları çalıştırmak tüm kullanıcıların sağlamak için 80 numaralı bağlantı noktası için genel olarak erişilebilir bir ayırma oluşturur. Bu ayırma ACL herkes için olduğundan, yöneticileri izin açıkça olamaz veya bir URL veya URL'ler kümesi dinlemek için izin vermeyin. Bu konuda bu ayırmayı silmek nasıl ve ayırma kısıtlı ACL ile yeniden oluşturma açıklanmaktadır.  
  
 Üzerinde [!INCLUDE[wv](../../../../includes/wv-md.md)] veya [!INCLUDE[lserver](../../../../includes/lserver-md.md)] tüm HTTP URL ayırmalarını yükseltilmiş bir komut isteminden yazarak görüntüle `netsh http show urlacl`.  Aşağıdaki örnek, ne WCF URL ayırmayı benzemelidir gösterir.  
  
```  
Reserved URL : http://+:80/Temporary_Listen_Addresses/  
        User: \Everyone  
            Listen: Yes  
            Delegate: No  
            SDDL: D:(A;;GX;;;WD)  
```  
  
 WCF uygulaması çift yönlü iletişim için HTTP çift bağlama kullanılırken kullanılan URL şablonu ayırma oluşur. Bu form URL'lerini için bir WCF hizmeti iletileri WCF HTTP çift bağlama üzerinden iletişim kurarken istemciye göndermek için kullanılır. Herkes URL üzerinde dinleme ancak başka bir işleme dinleme temsilci değil için izin verilir. Son olarak, ACL Güvenlik Tanımlayıcısı Tanım Dili (SSDL) açıklanmıştır. SSDL hakkında daha fazla bilgi için bkz: [SSDL](http://go.microsoft.com/fwlink/?LinkId=136789)  
  
### <a name="to-delete-the-wcf-url-reservation"></a>WCF URL ayırmayı silmek için  
  
1.  ' I tıklatın **Başlat**, işaret **tüm programlar**, tıklatın **Donatılar**, sağ tıklatın **komut istemi** tıklatıp **farklı çalıştır Yönetici** bağlam menüsünde gelir. Tıklatın **devam** kullanıcı hesabı denetimi (UAC) penceresinde, devam etmek için izinleri isteyebilir.  
  
2.  Yazın **netsh http delete urlacl url =http://+:80/Temporary_Listen_Addresses/**  komut istemi penceresinde.  
  
3.  Ayırma başarıyla silinirse, aşağıdaki ileti görüntülenir. **URL ayırma başarıyla silindi**  
  
## <a name="creating-a-new-security-group-and-new-restricted-url-reservation"></a>Yeni güvenlik grubu ve yeni kısıtlı URL ayırma oluşturma  
 WCF URL ayırmayı kısıtlı ayırma ile değiştirmek için yeni bir güvenlik grubu oluşturun. Bunu iki yoldan biriyle yapabilirsiniz: komut satırından veya Bilgisayar Yönetimi konsolu. Yalnızca birini yapmanız gerekir.  
  
#### <a name="to-create-a-new-security-group-from-a-command-prompt"></a>Bir komut isteminden yeni bir güvenlik grubu oluşturmak için  
  
1.  ' I tıklatın **Başlat**, işaret **tüm programlar**, tıklatın **Donatılar**, sağ tıklatın **komut istemi** tıklatıp **farklı çalıştır Yönetici** bağlam menüsünde gelir. Tıklatın **devam** kullanıcı hesabı denetimi (UAC) penceresinde, devam etmek için izinleri isteyebilir.  
  
2.  Yazın **net localgroup "\<güvenlik grubu adı >" / Açıklama: "\<güvenlik grubu açıklaması >" / add** komut isteminde. Değiştirme  **\<güvenlik grubu adı >** oluşturmak istediğiniz güvenlik grubunun adını ve  **\<güvenlik grubu açıklaması >** için uygun bir açıklama ile güvenlik grubu.  
  
3.  Güvenlik grubu başarıyla oluşturulduysa, aşağıdaki ileti görüntülenir. **Komutu başarıyla tamamlandı.**  
  
#### <a name="to-create-a-new-security-group-from-the-computer-management-console"></a>Bilgisayar Yönetimi konsolundan yeni bir güvenlik grubu oluşturmak için  
  
1.  ' I tıklatın **Başlat**, tıklatın **Denetim Masası**, tıklatın **Yönetimsel Araçlar**, tıklatıp **Bilgisayar Yönetimi** bilgisayarı açmak için Yönetim Konsolu. Tıklatın **devam** kullanıcı hesabı denetimi (UAC) penceresinde, devam etmek için izinleri isteyebilir.  
  
2.  Tıklatın **Sistem Araçları**, tıklatın **yerel kullanıcılar ve gruplar**, sağ tıklatın **grupları** klasörü ve tıklatın **yeni grup** bağlam menüsünde, gelir. İstenen türü **grup adı**, **açıklama** ve bu yeni güvenlik grubu ve tıklatın diğer ayrıntılarını **oluşturma** güvenlik grubu oluşturmak için düğmesini.  
  
#### <a name="to-create-the-restricted-url-reservation"></a>Kısıtlı URL ayırması oluşturmak için  
  
1.  ' I tıklatın **Başlat**, işaret **tüm programlar**, tıklatın **Donatılar**, sağ tıklatın **komut istemi** tıklatıp **farklı çalıştır Yönetici** bağlam menüsünde gelir. Tıklatın **devam** kullanıcı hesabı denetimi (UAC) penceresinde, devam etmek için izinleri isteyebilir.  
  
2.  Yazın **netsh http add urlacl url =http://+:80/Temporary_Listen_Addresses/ kullanıcı = "\<makine adı >\\< güvenlik grubu adı\>**  komut isteminde. Değiştirme  **\<makine adı >** grubu oluşturulmalıdır bilgisayar adıyla ve  **\<güvenlik grubu adı >** oluşturduğunuz güvenlik grubunun adı daha önce.  
  
3.  Ayırma başarıyla oluşturulduysa, aşağıdaki ileti görüntülenir. **URL ayırma başarıyla eklendi**.
