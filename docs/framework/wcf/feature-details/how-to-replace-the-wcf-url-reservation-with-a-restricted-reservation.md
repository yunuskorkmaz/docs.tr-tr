---
title: "Nasıl yapılır: WCF URL Ayırmayı Kısıtlı Ayırma ile Değiştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2754d223-79fc-4e2b-a6ce-989889f2abfa
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8c25403f298444732f6787979add595bd877bb2c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation"></a>Nasıl yapılır: WCF URL Ayırmayı Kısıtlı Ayırma ile Değiştirme
Bir URL ayırmasını URL'yi veya URL'leri kümesini kimin ileti alabilir kısıtlamak sağlar. Bir ayırma bir URL şablonu, bir erişim denetimi listesi (ACL) ve bir dizi bayrakları oluşur. URL şablonu ayırma etkiler hangi URL'leri tanımlar. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]URL şablonları işlenen bkz [yönlendirme gelen istekleri](http://go.microsoft.com/fwlink/?LinkId=136764). Belirtilen URL'lerden iletileri almak için hangi kullanıcı veya kullanıcı grubuna izin ACL denetler. Bayrakları ayırma URL üzerinde doğrudan dinlemek veya başka bir işlem dinlemek için temsilci izni verme için bir kullanıcı veya grup izin vermek için olup olmadığını belirtin.  
  
 Varsayılan işletim sistemi yapılandırma, bir parçası olarak [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] çift yönlü iletişim için çift HTTP bağlama kullanan uygulamaları çalıştırmak tüm kullanıcıların sağlamak için 80 numaralı bağlantı noktası için genel olarak erişilebilir bir ayırma oluşturur. Bu ayırma ACL herkes için olduğundan, yöneticileri izin açıkça olamaz veya bir URL veya URL'ler kümesi dinlemek için izin vermeyin. Bu konuda bu ayırmayı silmek nasıl ve ayırma kısıtlı ACL ile yeniden oluşturma açıklanmaktadır.  
  
 Üzerinde [!INCLUDE[wv](../../../../includes/wv-md.md)] veya [!INCLUDE[lserver](../../../../includes/lserver-md.md)] tüm HTTP URL ayırmalarını yükseltilmiş bir komut isteminden yazarak görüntüle `netsh http show urlacl`.  Aşağıdaki örnek ne gösterir bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] URL ayırmasını benzer.  
  
```  
Reserved URL : http://+:80/Temporary_Listen_Addresses/  
        User: \Everyone  
            Listen: Yes  
            Delegate: No  
            SDDL: D:(A;;GX;;;WD)  
```  
  
 Bir URL ayırma oluşur şablonu kullanılan bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulama çift yönlü iletişim için HTTP çift bağlama kullanıyor. Bu formun URL'ler için kullanılır bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iletileri yeniden göndermek için hizmet [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] HTTP çift bağlama üzerinden iletişim kurarken istemci. Herkes URL üzerinde dinleme ancak başka bir işleme dinleme temsilci değil için izin verilir. Son olarak, ACL Güvenlik Tanımlayıcısı Tanım Dili (SSDL) açıklanmıştır. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]SSDL, bkz: [SSDL](http://go.microsoft.com/fwlink/?LinkId=136789)  
  
### <a name="to-delete-the-wcf-url-reservation"></a>WCF URL ayırmayı silmek için  
  
1.  ' I tıklatın **Başlat**, işaret **tüm programlar**, tıklatın **Donatılar**, sağ tıklatın **komut istemi** tıklatıp **farklı çalıştır Yönetici** bağlam menüsünde gelir. Tıklatın **devam** kullanıcı hesabı denetimi (UAC) penceresinde, devam etmek için izinleri isteyebilir.  
  
2.  Yazın **netsh http delete urlacl url = http: / / +:80/Temporary_Listen_Addresses/** komut istemi penceresinde.  
  
3.  Ayırma başarıyla silinirse, aşağıdaki ileti görüntülenir. **URL ayırma başarıyla silindi**  
  
## <a name="creating-a-new-security-group-and-new-restricted-url-reservation"></a>Yeni güvenlik grubu ve yeni kısıtlı URL ayırma oluşturma  
 Değiştirmek için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] URL ayırmayı kısıtlı ayırma ile yeni bir güvenlik grubu önce oluşturmanız gerekir. Bunu iki yoldan biriyle yapabilirsiniz: komut satırından veya Bilgisayar Yönetimi konsolu. Yalnızca birini yapmanız gerekir.  
  
#### <a name="to-create-a-new-security-group-from-a-command-prompt"></a>Bir komut isteminden yeni bir güvenlik grubu oluşturmak için  
  
1.  ' I tıklatın **Başlat**, işaret **tüm programlar**, tıklatın **Donatılar**, sağ tıklatın **komut istemi** tıklatıp **farklı çalıştır Yönetici** bağlam menüsünde gelir. Tıklatın **devam** kullanıcı hesabı denetimi (UAC) penceresinde, devam etmek için izinleri isteyebilir.  
  
2.  Yazın **net localgroup "\<güvenlik grubu adı >" / Açıklama: "\<güvenlik grubu açıklaması >" / add** komut isteminde. Değiştirme  **\<güvenlik grubu adı >** oluşturmak istediğiniz güvenlik grubunun adını ve  **\<güvenlik grubu açıklaması >** için uygun bir açıklama ile güvenlik grubu.  
  
3.  Güvenlik grubu başarıyla oluşturulduysa, aşağıdaki ileti görüntülenir. **Komutu başarıyla tamamlandı.**  
  
#### <a name="to-create-a-new-security-group-from-the-computer-management-console"></a>Bilgisayar Yönetimi konsolundan yeni bir güvenlik grubu oluşturmak için  
  
1.  ' I tıklatın **Başlat**, tıklatın **Denetim Masası**, tıklatın **Yönetimsel Araçlar**, tıklatıp **Bilgisayar Yönetimi** bilgisayarı açmak için Yönetim Konsolu. Tıklatın **devam** kullanıcı hesabı denetimi (UAC) penceresinde, devam etmek için izinleri isteyebilir.  
  
2.  Tıklatın **Sistem Araçları**, tıklatın **yerel kullanıcılar ve gruplar**, sağ tıklatın **grupları** klasörü ve tıklatın **yeni grup** bağlam menüsünde, gelir. İstenen türü **grup adı**, **açıklama** ve bu yeni güvenlik grubu ve tıklatın diğer ayrıntılarını **oluşturma** güvenlik grubu oluşturmak için düğmesini.  
  
#### <a name="to-create-the-restricted-url-reservation"></a>Kısıtlı URL ayırması oluşturmak için  
  
1.  ' I tıklatın **Başlat**, işaret **tüm programlar**, tıklatın **Donatılar**, sağ tıklatın **komut istemi** tıklatıp **farklı çalıştır Yönetici** bağlam menüsünde gelir. Tıklatın **devam** kullanıcı hesabı denetimi (UAC) penceresinde, devam etmek için izinleri isteyebilir.  
  
2.  Yazın **netsh http add urlacl url = http: / / +: 80/Temporary_Listen_Addresses/kullanıcı = "\<makine adı >\\< güvenlik grubu adı\>**  komut isteminde. Değiştirme  **\<makine adı >** grubu oluşturulmalıdır bilgisayar adıyla ve  **\<güvenlik grubu adı >** oluşturduğunuz güvenlik grubunun adı daha önce.  
  
3.  Ayırma başarıyla oluşturulduysa, aşağıdaki ileti görüntülenir. **URL ayırma başarıyla eklendi**.
