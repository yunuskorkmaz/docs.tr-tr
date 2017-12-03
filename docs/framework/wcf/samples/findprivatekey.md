---
title: FindPrivateKey
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: FindPrivateKey
ms.assetid: 16b54116-0ceb-4413-af0c-753bb2a785a6
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 81ca357ccdcbe76f36f3ba56caf2013a80143728
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="findprivatekey"></a>FindPrivateKey
Belirli bir X.509 sertifikası sertifika deposunda ilişkili özel anahtar dosyasının adını ve konumunu bulmak zor olabilir. FindPrivateKey.exe aracı bu işlemi kolaylaştırır.  
  
> [!IMPORTANT]
>  FindPrivateKey kullanmak için derlenmiş önceki olması gereken bir örnektir. FindPrivateKey aracı derleme hakkında yönergeler için aşağıdaki "FindPrivateKey projeyi oluşturmak için" bölümüne bakın.  
  
 X.509 sertifikaları, bir yönetici veya makinede herhangi bir kullanıcı tarafından yüklenir. Ancak sertifika başka bir hesap altında çalışan bir hizmete erişebilir (örneğin, ASP.NET üzerinde [!INCLUDE[wxp](../../../../includes/wxp-md.md)] veya ağ hizmeti hesaplarında [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]).  
  
 Sertifika tarafından başlangıçta yüklenmediğinden bu hesap için özel anahtar dosyası erişimi olmayabilir. FindPrivateKey aracı bir verilen X.509 sertifikasının özel anahtar dosyasının konumunu sağlar. İzinleri eklemek veya bu dosyaya izinleri belirli X.509 sertifikalarının özel anahtar dosyasının konumunu öğrendikten sonra kaldırın.  
  
 Güvenlik için sertifikaları kullanma örnekleri Setup.bat dosyasında FindPrivateKey aracını kullanın. Özel anahtar dosyası bulunamadı sonra uygun erişim haklarını dosyanın ayarlamak için Cacls.exe gibi diğer araçları kullanabilirsiniz.  
  
 Çalıştırırken bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] kendini barındıran bir yürütülebilir dosya gibi bir kullanıcı hesabı altında service, kullanıcı hesabının dosyaya salt okunur erişim bulunduğundan emin olun. Çalıştırırken bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] altında Internet Information Services (hizmetinin altında çalıştığı için varsayılan hesaplar olan ASPNET IIS) hizmetini [!INCLUDE[wxp](../../../../includes/wxp-md.md)] veya ağ hizmeti üzerinde [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], varsayılan olarak erişimi yoktur özel anahtar dosyası.  
  
## <a name="examples"></a>Örnekler  
 İşlemi okuma ayrıcalığı olmayan bir sertifika erişirken, aşağıdaki örneğe benzer bir özel durum iletisi görürsünüz.  
  
```  
System.ArgumentException was unhandled  
Message="The certificate 'CN=localhost' must have a private key that is capable of key exchange.  The process must have access rights for the private key."  
Source="System.ServiceModel"  
```  
  
 Bu durumda özel anahtar dosyasını bulun ve ardından sağ hizmetinin altında çalışan işlemi için erişim için FindPrivateKey aracını kullanın. Örneğin, bu Cacls.exe aracıyla aşağıdaki örnekte gösterildiği gibi yapılabilir.  
  
```  
cacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /E /G "NETWORK SERVICE":R  
```  
  
#### <a name="to-build-the-findprivatekey-project"></a>FindPrivateKey projeyi oluşturmak için  
  
1.  Açık [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] ve örnek yüklendiği dizin konumu altında dile özgü alt dizine gidin.  
  
2.  Visual Studio'da dosyayı açmaya .sln dosyasını simgesini çift tıklatın.  
  
3.  İçinde **yapı** menüsünde, select **çözümü yeniden derle**. İstemci program dosyaları için client\bin yerleşiktir ve hizmet program dosyaları için service\bin oluşturulur.  
  
4.  Çözümü derleme dosyası oluşturur: FindPrivateKey.exe.  
  
## <a name="conventionscommand-line-entries"></a>Kuralları — komut satırı girişleri  
 "[*seçeneği*]" bir isteğe bağlı parametreleri kümesini temsil eder.  
  
 "{*seçeneği*}" parametreleri zorunlu kümesini temsil eder.  
  
 "*seçenek 1* &#124; *Seçenek2*"seçenekleri kümesi arasında bir seçim temsil eder.  
  
 "\<*değeri*>" girilecek bir parametre değerini temsil eder.  
  
## <a name="usage"></a>Kullanım  
  
```  
FindPrivateKey <storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]  
```  
  
 Konum:  
  
```  
       <subjectName> The subject name of the certificate  
       <thumbprint>  The thumbprint of the certificate (You can use the Certmgr.exe tool to find this)  
       -f            output file name only  
       -d            output directory only  
       -a            output absolute file name  
```  
  
 Komut isteminde hiçbir parametre belirtilmezse, bu Yardım metni görüntülenir.  
  
## <a name="examples"></a>Örnekler  
 Bu örnek sertifika filename konu adıyla bulur "CN = localhost", kişisel deposunda geçerli User.FindPrivateKey My Currentuser'a - n "CN = localhost".  
  
 Bu örnek sertifika filename konu adıyla bulur "CN = localhost", Kişisel depolama geçerli ve tam dizin yolu çıktı.  
  
```  
User.FindPrivateKey My CurrentUser -n "CN=localhost" -a  
```  
  
 Bu örnek dosya adının sertifikanın parmak izi bulur "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1 d 6b 52", yerel bilgisayarın kişisel deposunda.  
  
```  
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" –c  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.
