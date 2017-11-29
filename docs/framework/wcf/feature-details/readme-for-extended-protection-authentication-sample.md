---
title: "Genişletilmiş Koruma Kimlik Doğrulama için Beni Oku Örnek"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 80bf2e97-398d-4db5-9040-d96478a2ccab
caps.latest.revision: "3"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 3981a0d0c82b8bc35536a9afd702e753fcf07db5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="readme-for-extended-protection-authentication-sample"></a>Genişletilmiş Koruma Kimlik Doğrulama için Beni Oku Örnek
Genişletilmiş koruma, bir saldırgan ("man-in--middle") istemci kimlik bilgilerini yakalar ve bunları istemcinin hedeflenen sunucuda güvenlikli kaynaklara erişmek için kullandığı man-in--middle (MITM) saldırılarına karşı korumak için bir güvenlik girişimidir.  
  
 Daha fazla bilgi için bkz: [kimlik doğrulamasına genel bakış için genişletilmiş koruma](../../../../docs/framework/wcf/feature-details/extended-protection-for-authentication-overview.md).  
  
> [!NOTE]
>  Bu örnek yalnızca IIS üzerinde barındırıldığında çalışır. HTTPS desteklemediği için Visual Studio geliştirme sunucusu üzerinde çalışmıyor.  
  
## <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Program Ekle/Kaldır makinede yükleme IIS -> Windows özelliklerini.  
  
2.  Windows özelliklerinde Windows kimlik doğrulamasını etkinleştirmek: Internet Information Services World Wide Web Hizmetleri -> Güvenlik -> Windows kimlik doğrulaması ->.  
  
3.  HTTP etkinleştirme Windows özelliklerini aç: Microsoft .NET Framework 3.5.1 -> Windows Communication Foundation HTTP etkinleştirme.  
  
4.  Bu örnek sunucu ile güvenli bir kanal oluşturmak için istemcinin gerektirir ve bu nedenle, Internet Information Services (IIS) Yöneticisi'nden yüklenebilecek bir sunucu sertifikası varlığını gerektirir.  
  
    1.  Açık IIS Yöneticisi'ni -> sunucu sertifikaları (sekmesinden özelliği Görünüm).  
  
    2.  Bu örnek test amacıyla, otomatik olarak imzalanan sertifika oluşturabilirsiniz. (Internet Explorer'ı güvenli olmadığı sertifika hakkında soracak şekilde istemiyorsanız, güvenilen kök sertifika yetkilisi depolarında yükleyebilirsiniz).  
  
5.  Varsayılan Web sitesi için Eylemler bölmesine gidin. Düzenle'yi tıklatın Site bağlamaları ->. HTTPS türü olarak zaten değilse, bağlantı noktası numarası 443 sunmak ve Yukarıdaki adımda oluşturulan SSL sertifika atama ekleyin.  
  
6.  Hizmet oluşturun. Bu sanal dizin IIS'de sizin için (eylemden proje özelliklerinde belirtilen post yapı) oluşturur ve barındırılan Web olması için bir hizmet için gerektiği şekilde dll, .svc ve yapılandırma dosyalarını kopyalar.  
  
7.  IIS Yöneticisi'ni açın. Önceki adımda oluşturduğunuz sanal dizinini (ExtendedProtection) sağ tıklatın ve uygulama Dönüştür seçin.  
  
8.  Kimlik doğrulama modülü bu sanal dizin için IIS Yöneticisi'nde açın ve Windows kimlik doğrulamasını etkinleştirin.  
  
9. Gelişmiş ayarlar için Windows kimlik doğrulaması için bu sanal dizin açın ve aşağıdaki örnekte, her zaman karşılık gelen ExtendedProtection ayarı ayarlandığından, gerekli ayarlayın.  
  
10. Hizmet URL'sini bir tarayıcı penceresinde erişerek test edebilirsiniz. Bu URL çapraz bir makineden erişmek Güvenlik Duvarı tüm gelen HTTP ve HTTPS bağlantıları için açıldığında emin olun.  
  
11. İstemci yapılandırma dosyasını açın ve için tam makine ad \<istemci >- \<uç noktası >-adresi özniteliğinin, << full_machine_name >> değiştirme.  
  
12. İstemciyi çalıştırın. İstemci hizmete güvenli bir kanal oluşturma ve genişletilmiş koruma kapsar altında kullanarak iletişim kurar.
