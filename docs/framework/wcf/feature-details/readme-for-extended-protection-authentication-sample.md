---
description: 'Daha fazla bilgi edinin: genişletilmiş koruma kimlik doğrulama örneği için ReadMe'
title: Genişletilmiş Koruma Kimlik Doğrulama için Beni Oku Örnek
ms.date: 03/30/2017
ms.assetid: 80bf2e97-398d-4db5-9040-d96478a2ccab
ms.openlocfilehash: edab04c7762bf8964f634107debd3de35a7702ab
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99733313"
---
# <a name="readme-for-extended-protection-authentication-sample"></a>Genişletilmiş Koruma Kimlik Doğrulama için Beni Oku Örnek

Genişletilmiş koruma, bir saldırganın ("ortadaki adam") bir istemcinin kimlik bilgilerini aldığı ve istemcinin hedeflenen sunucusundaki güvenli kaynaklara erişmek için bunları kullandığı, ortadaki adam (MITı) saldırılarına karşı koruma sağlayan bir güvenlik girişimidir.

Daha fazla bilgi için bkz. [kimlik doğrulaması için genişletilmiş koruma genel bakış](extended-protection-for-authentication-overview.md).

> [!NOTE]
> Bu örnek yalnızca IIS üzerinde barındırıldığında geçerlidir. Bu, HTTPS 'yi desteklemediğinden, Visual Studio geliştirme sunucusu üzerinde çalışmaz.

## <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için

1. Program Ekle/Kaldır-> Windows Özellikleri ' nden makineye IIS 'yi yükler.

2. Windows özelliklerinde Windows kimlik doğrulamasını aç: Internet Information Services > World Wide Web Hizmetleri-> güvenlik-> Windows kimlik doğrulaması.

3. Windows özelliklerinde HTTP etkinleştirmesini aç: Microsoft .NET Framework 3.5.1-> Windows Communication Foundation HTTP etkinleştirmesi.

4. Bu örnek, istemcisinin sunucu ile güvenli bir kanal kurmasını ve bu nedenle Internet Information Services (IIS) yöneticisinden yüklenebilen bir sunucu sertifikası olması gerekir.

    1. IIS Yöneticisi-> sunucusu sertifikalarını açın (Özellik görünümü sekmesinden).

    2. Bu örneği test etmek amacıyla kendinden imzalı bir sertifika oluşturabilirsiniz. (Internet Explorer 'ın sertifikayı güvenli hale getirmek için size sormasını istemiyorsanız, güvenilir sertifika kök yetkilisi deposuna yükleyebilirsiniz).

5. Varsayılan Web sitesi için eylemler bölmesine gidin. Site > bağlamalarını Düzenle ' ye tıklayın. Zaten mevcut değilse HTTPS 'yi bir tür olarak ekleyin, bağlantı noktası numarası 443 ve yukarıdaki adımda oluşturulan SSL sertifikasını atayın.

6. Hizmeti oluşturun. Bu, IIS 'de sizin için bir sanal dizin oluşturur (proje özelliklerinde belirtilen derleme sonrası eyleminden) ve bir hizmetin Web 'de barındırılması için gerektiğinde dll,. svc ve yapılandırma dosyalarını kopyalar.

7. IIS Yöneticisi 'Ni açın. Önceki adımda oluşturduğunuz sanal dizine (ExtendedProtection) sağ tıklayın ve uygulamaya Dönüştür ' ü seçin.

8. Bu sanal dizin için IIS Yöneticisi 'nde kimlik doğrulama modülünü açın ve Windows kimlik doğrulamasını etkinleştirin.

9. Bu sanal dizin için Windows kimlik doğrulaması için Gelişmiş ayarlar ' ı açın ve gerekli olarak ayarlayın, çünkü örnekte ilgili ExtendedProtection ayarı her zaman olarak ayarlanır.

10. Bir tarayıcı penceresinden URL 'ye erişerek hizmeti test edebilirsiniz. Bu URL 'YI bir çapraz makineden erişmek istiyorsanız, tüm gelen HTTP ve HTTPS bağlantıları için güvenlik duvarının açık olduğundan emin olun.

11. İstemci yapılandırma dosyasını açın ve \<client>  -  \<endpoint> yerine-address özniteliği için tam makine adı girin \<full_machine_name> .

12. İstemcisini çalıştırın. İstemci, güvenli bir kanal kurarak ve bunların altında genişletilmiş koruma kullanarak hizmetle iletişim kurar.
