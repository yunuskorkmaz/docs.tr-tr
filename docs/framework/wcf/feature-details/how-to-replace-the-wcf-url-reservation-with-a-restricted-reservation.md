---
title: 'Nasıl yapılır: WCF URL Ayırmayı Kısıtlı Ayırma ile Değiştirme'
ms.date: 03/30/2017
ms.assetid: 2754d223-79fc-4e2b-a6ce-989889f2abfa
ms.openlocfilehash: fc50a0e31a0c323b695ada6565743fa19c1d4c2a
ms.sourcegitcommit: 09b4090b78f52fd09b0e430cd4b26576f1fdf96e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76212184"
---
# <a name="how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation"></a>Nasıl yapılır: WCF URL Ayırmayı Kısıtlı Ayırma ile Değiştirme

URL ayırması, URL 'lerden veya URL kümesinden ileti alabilen kişileri kısıtlayabilmeniz için izin verir. Bir ayırma, bir URL şablonundan, erişim denetim listesinden (ACL) ve bir bayrak kümesinden oluşur. URL şablonu, rezervasyonun etkilediği URL 'Leri tanımlar. URL şablonlarının nasıl işlendiği hakkında daha fazla bilgi için bkz. [gelen Istekleri yönlendirme](/windows/win32/http/routing-incoming-requests). ACL, hangi kullanıcı veya Kullanıcı grubunun belirtilen URL 'lerden ileti almasına izin verileceğini denetler. Bayraklar, rezervasyonun bir kullanıcıya veya gruba doğrudan URL 'yi dinlemek için ya da başka bir işlemi dinlemek için izin vermek için izin verip vermeyeceğinizi belirtir.  
  
 Varsayılan işletim sistemi yapılandırması kapsamında, Windows Communication Foundation (WCF), tüm kullanıcıların çift yönlü iletişim için çift HTTP bağlaması kullanan uygulamaları çalıştırmasını sağlamak üzere 80 numaralı bağlantı noktası için genel olarak erişilebilen bir ayırma oluşturur. Bu ayırmayla ilgili ACL herkes için olduğundan, yöneticiler bir URL 'yi veya URL kümesini dinlemek için açıkça izin vermeyebilir veya izin vermez. Bu konu, bu ayırmayı silmenin yanı sıra kısıtlı ACL ile ayırmayı yeniden oluşturmayı açıklar.  
  
Windows Vista veya Windows Server 2008 ' de, `netsh http show urlacl`girerek yükseltilmiş bir komut isteminden HTTP URL ayırmalarını görüntüleyebilirsiniz. Aşağıdaki örnek, bir WCF URL ayırmasını şuna benzemesi gerektiğini gösterir:

```
Reserved URL : http://+:80/Temporary_Listen_Addresses/  
        User: \Everyone  
            Listen: Yes  
            Delegate: No  
            SDDL: D:(A;;GX;;;WD)  
```

 Ayırma, bir WCF uygulaması çift yönlü iletişim için HTTP çift bağlamayı kullanırken kullanılan bir URL şablonundan oluşur. Bu formun URL 'Leri, bir WCF hizmeti için HTTP Dual Binding üzerinden iletişim kurarken iletileri WCF istemcisine geri göndermek için kullanılır. Herkese, URL 'yi dinlemek için izin verilir, ancak başka bir işleme dinlemeyi devretmek için izin verilmez. Son olarak, ACL güvenlik tanımlayıcısı tanım dili (SSDL) içinde açıklanır. SSDL hakkında daha fazla bilgi için bkz. [SSDL](/windows/win32/secauthz/security-descriptor-definition-language)  
  
## <a name="to-delete-the-wcf-url-reservation"></a>WCF URL ayırmasını silmek için  
  
1. **Başlat**' a tıklayın, **tüm programlar**' ın üzerine gelin, **Donatılar**' a tıklayın, **komut istemi** ' ne sağ tıklayın ve açılan bağlam menüsünde **yönetici olarak çalıştır** ' a tıklayın. Kullanıcı hesabı denetimi (UAC) penceresinde, devam etmek için izinleri sorabileceğiniz **devam** ' a tıklayın.  
  
2. Komut istemi penceresinde **netsh http Delete urlacl URL =http://+:80/Temporary_Listen_Addresses/** yazın.  
  
3. Ayırma başarıyla silinirse, aşağıdaki ileti görüntülenir. **URL ayırması başarıyla silindi**  
  
## <a name="creating-a-new-security-group-and-new-restricted-url-reservation"></a>Yeni bir güvenlik grubu ve yeni kısıtlanmış URL ayırması oluşturma  
 WCF URL ayırmasını kısıtlı bir rezervasyon ile değiştirmek için, önce yeni bir güvenlik grubu oluşturmanız gerekir. Bunu iki şekilde yapabilirsiniz: bir komut isteminden veya bilgisayar yönetim konsolundan. Yalnızca bir tane yapmanız gerekir.  
  
### <a name="to-create-a-new-security-group-from-a-command-prompt"></a>Komut isteminden yeni bir güvenlik grubu oluşturmak için  
  
1. **Başlat**' a tıklayın, **tüm programlar**' ın üzerine gelin, **Donatılar**' a tıklayın, **komut istemi** ' ne sağ tıklayın ve açılan bağlam menüsünde **yönetici olarak çalıştır** ' a tıklayın. Kullanıcı hesabı denetimi (UAC) penceresinde, devam etmek için izinleri sorabileceğiniz **devam** ' a tıklayın.  
  
2. **Net localgroup "\<güvenlik grubu adı >"/Comment: "\<güvenlik grubu açıklaması >"/Add** komut isteminde yazın. **\<güvenlik grubu adı >** , oluşturmak istediğiniz güvenlik grubunun adı ve güvenlik grubu **açıklaması >\<** güvenlik grubu için uygun bir açıklama ile değiştirin.  
  
3. Güvenlik grubu başarıyla oluşturulursa, aşağıdaki ileti görüntülenir. **Komut başarıyla tamamlandı.**  
  
### <a name="to-create-a-new-security-group-from-the-computer-management-console"></a>Bilgisayar yönetim konsolundan yeni bir güvenlik grubu oluşturmak için  
  
1. **Başlat**' a tıklayın, **Denetim Masası**' na tıklayın, **Yönetimsel Araçlar**' a tıklayın ve bilgisayar **yönetimi** ' ne tıklayarak Bilgisayar Yönetimi konsolunu açın. Kullanıcı hesabı denetimi (UAC) penceresinde, devam etmek için izinleri sorabileceğiniz **devam** ' a tıklayın.  
  
2. **Sistem Araçları**' na tıklayın **, yerel kullanıcılar ve gruplar**' a tıklayın, **gruplar** klasörüne sağ tıklayın ve ardından gelen bağlam menüsünde **Yeni Grup** ' a tıklayın. İstenen **Grup adı**, **Açıklama** ve bu yeni güvenlik grubunun diğer ayrıntılarını yazın ve güvenlik grubunu oluşturmak için **Oluştur** düğmesine tıklayın.  
  
### <a name="to-create-the-restricted-url-reservation"></a>Kısıtlanmış URL ayırmayı oluşturmak için  
  
1. **Başlat**' a tıklayın, **tüm programlar**' ın üzerine gelin, **Donatılar**' a tıklayın, **komut istemi** ' ne sağ tıklayın ve açılan bağlam menüsünde **yönetici olarak çalıştır** ' a tıklayın. Kullanıcı hesabı denetimi (UAC) penceresinde, devam etmek için izinleri sorabileceğiniz **devam** ' a tıklayın.  
  
2. **Netsh http Add urlacl URL =http://+:80/Temporary_Listen_Addresses/ user = "\< makine adı >\\ < güvenlik grubu adı\>** komut istemine yazın. **\<makine adı >** , grubun oluşturulması gereken bilgisayar adıyla ve **güvenlik grubu adı >\<** daha önce oluşturduğunuz güvenlik grubunun adıyla değiştirin.  
  
3. Rezervasyon başarıyla oluşturulursa, aşağıdaki ileti görüntülenir. **URL ayırması başarıyla eklendi**.
