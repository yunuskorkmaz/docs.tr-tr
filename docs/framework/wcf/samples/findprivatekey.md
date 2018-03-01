---
title: "FindPrivateKey örnek - WCF"
ms.date: 12/04/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
helpviewer_keywords:
- FindPrivateKey
ms.assetid: 16b54116-0ceb-4413-af0c-753bb2a785a6
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 32e1a4a3de01371d67be8d19613b1f29c1ce3c29
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="findprivatekey-sample"></a>FindPrivateKey örnek

Belirli bir X.509 sertifikası sertifika deposunda ilişkili özel anahtar dosyasının adını ve konumunu bulmak zor olabilir. FindPrivateKey.exe aracı bu işlemi kolaylaştırır.

> [!IMPORTANT]
> FindPrivateKey kullanmak için derlenmiş önceki olması gereken bir örnektir. Bkz: [FindPrivateKey Projeyi derlemek için](#to-build-the-findprivatekey-project) bölüm FindPrivateKey aracını yapılandırma hakkında yönergeler için.

X.509 sertifikaları, bir yönetici veya makinede herhangi bir kullanıcı tarafından yüklenir. Ancak, sertifika başka bir hesap altında çalışan bir hizmete erişebilir. Örneğin, ağ hizmeti hesabı.

Sertifika tarafından başlangıçta yüklenmediğinden bu hesap için özel anahtar dosyası erişimi olmayabilir. FindPrivateKey aracı bir verilen X.509 sertifikasının özel anahtar dosyasının konumunu sağlar. İzinleri eklemek veya bu dosyaya izinleri belirli X.509 sertifikalarının özel anahtar dosyasının konumunu öğrendikten sonra kaldırın.

Güvenlik için sertifikaları kullanma örnekleri FindPrivateKey aracını *Setup.bat* dosya. Özel anahtar dosyası bulunamadı sonra gibi diğer araçları kullanarak *Cacls.exe* dosyanın uygun erişim haklarına ayarlanamadı.

Windows Communication Foundation (WCF) hizmetini kendini barındıran bir yürütülebilir dosya gibi bir kullanıcı hesabı altında çalışan kullanıcı hesabı dosyaya salt okunur erişimi olduğundan emin olun. Bir WCF hizmeti Internet Information Services (IIS) altında çalışırken, altında çalışacağı varsayılan IIS 7 ve önceki sürümlerde ağ hizmet veya uygulama havuzu kimliği IIS 7.5 ve sonraki sürümlerde hesaplarıdır. Daha fazla bilgi için bkz: [uygulama havuzu kimlikleri](/iis/manage/configuring-security/application-pool-identities).

## <a name="examples"></a>Örnekler

İşlem okuma ayrıcalığına sahip olmayan bir sertifika erişirken, aşağıdaki örneğe benzer bir özel durum iletisi bakın:

```
System.ArgumentException was unhandled
Message="The certificate 'CN=localhost' must have a private key that is capable of key exchange.  The process must have access rights for the private key."
Source="System.ServiceModel"
```

Bu durumda, özel anahtar dosyasını bulmak için FindPrivateKey aracını kullanın ve ardından erişim hakkı hizmetinin altında çalışan işlemi için ayarlayın. Örneğin, bu Cacls.exe aracıyla aşağıdaki örnekte gösterildiği gibi yapılabilir:

```
cacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /E /G "NETWORK SERVICE":R
```

#### <a name="to-build-the-findprivatekey-project"></a>FindPrivateKey projeyi oluşturmak için

Proje indirmek için şurayı ziyaret edin [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](https://www.microsoft.com/download/details.aspx?id=21459).

1. Açık [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] gidin *WF_WCF_Samples\WCF\Setup\FindPrivateKey\CS* örnek yüklendiği dizin konumu altında bir klasör.

2. Visual Studio'da dosyayı açmaya .sln dosyasını simgesini çift tıklatın.

3. İçinde **yapı** menüsünde, select **çözümü yeniden derle**.

4. Çözümü derleme dosyası oluşturur: FindPrivateKey.exe.

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

Hiçbir parametre komut isteminde belirtilirse, bu Yardım metni görüntülenir.

## <a name="examples"></a>Örnekler

Bu örnek sertifika filename konu adıyla bulur "CN = localhost", geçerli kullanıcının kişisel deposunda.

```
FindPrivateKey My CurrentUser -n "CN=localhost"
```

Bu örnek sertifika filename konu adıyla bulur "CN = localhost", Kişisel depolama geçerli kullanıcının ve çıkış tam dizin yolu.

```
FindPrivateKey My CurrentUser -n "CN=localhost" -a
```

Bu örnek dosya adının sertifikanın parmak izi bulur "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1 d 6b 52", yerel bilgisayarın kişisel deposunda.

```
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52"
```
