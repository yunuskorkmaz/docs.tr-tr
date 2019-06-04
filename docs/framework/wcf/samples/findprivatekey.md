---
title: FindPrivateKey örneği - WCF
ms.date: 12/04/2017
helpviewer_keywords:
- FindPrivateKey
ms.assetid: 16b54116-0ceb-4413-af0c-753bb2a785a6
ms.openlocfilehash: b89d135d7412f10cb9de1e4bda1aaab14b29cbf0
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490776"
---
# <a name="findprivatekey-sample"></a>FindPrivateKey örnek

Sertifika deposundaki belirli bir X.509 sertifikasıyla ilişkili özel anahtar dosyasının adını ve konumunu bulmak zor olabilir. FindPrivateKey.exe aracı bu işlemi kolaylaştırır.

> [!IMPORTANT]
> FindPrivateKey kullanmadan önce derlenmiş olması gereken bir örnektir. Bkz: [FindPrivateKey Projeyi derlemek için](#to-build-the-findprivatekey-project) bölüm derleme FindPrivateKey aracı hakkında yönergeler için.

X.509 sertifikalarına bir yönetici veya makinede bulunan herhangi bir kullanıcı tarafından yüklenir. Ancak, sertifika, farklı bir hesap altında çalışan bir hizmet tarafından erişilebilir. Örneğin, ağ hizmeti hesabı.

Bu hesap sertifikası tarafından başlangıçta yüklenmediğinden özel anahtar dosyasına erişimi olmayabilir. FindPrivateKey Aracı'nı bir verilen X.509 sertifikasının özel anahtar dosyasının konumunu sağlar. İzinleri eklemek veya belirli X.509 sertifikalarının özel anahtar dosyasının konumunu bilmek sonra bu dosyaya izinleri kaldırın.

Güvenlik için sertifikaları kullanma örnekleri FindPrivateKey aracını *Setup.bat* dosya. Özel anahtar dosyası bulunamadı sonra gibi diğer araçları kullanın *Cacls.exe* dosyasını uygun erişim haklarını ayarlanacak.

Bir Windows Communication Foundation (WCF) hizmet şirket içinde barındırılan bir yürütülebilir dosya gibi bir kullanıcı hesabı altında çalışıyorsa, kullanıcı hesabının dosyaya salt okunur erişimi olduğundan emin olun. Bir WCF hizmeti Internet Information Services (IIS) altında çalışırken hizmetin altında çalıştığı varsayılan IIS 7 ve önceki sürümlerde ağ hizmeti veya IIS 7.5 ve üzeri sürümler üzerinde uygulama havuzu kimliği hesaplarıdır. Daha fazla bilgi için [uygulama havuzu kimlikleri](/iis/manage/configuring-security/application-pool-identities).

## <a name="examples"></a>Örnekler

İşlemi okuma ayrıcalığına sahip değil bir sertifika erişirken, aşağıdaki örneğe benzer bir özel durum iletisi görürsünüz:

```
System.ArgumentException was unhandled
Message="The certificate 'CN=localhost' must have a private key that is capable of key exchange.  The process must have access rights for the private key."
Source="System.ServiceModel"
```

Bu durumda, özel anahtar dosyasını bulmak için FindPrivateKey aracını kullanın ve ardından sağ hizmetinin altında çalışmakta olduğu işlem için erişim ayarlayın. Örneğin, bu için Cacls.exe aracının aşağıdaki örnekte gösterildiği gibi yapılabilir:

```
cacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /E /G "NETWORK SERVICE":R
```

#### <a name="to-build-the-findprivatekey-project"></a>FindPrivateKey projeyi oluşturmak için

Projeyi indirmek için şurayı ziyaret edin [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://www.microsoft.com/download/details.aspx?id=21459).

1. Dosya Gezgini'ni açın ve gidin *WF_WCF_Samples\WCF\Setup\FindPrivateKey\CS* klasörü altında örnek yüklediğiniz dizin konumu.

2. Visual Studio'da dosyayı açmak için bir .sln dosya simgesini çift tıklatın.

3. İçinde **derleme** menüsünde **çözümü yeniden derle**.

4. Çözümü derledikten dosyası oluşturur: FindPrivateKey.exe.

## <a name="conventionscommand-line-entries"></a>Kuralları — komut satırı girişleri

 "[*seçeneği*]" isteğe bağlı parametrelerinin temsil eder.

 "{*seçeneği*}" zorunlu bir parametre kümesini temsil eder.

 "*option1* &#124; *option2*" represents a choice between sets of options.

 "\<*değer*>" girilmesi bir parametre değeri temsil eder.

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

Komut isteminde parametre belirtilirse, ardından bu Yardım metni görüntülenir.

## <a name="examples"></a>Örnekler

Bu örnek dosya adının sertifikanın konu adını bulur "CN = localhost", geçerli kullanıcının kişisel depoda.

```
FindPrivateKey My CurrentUser -n "CN=localhost"
```

Bu örnek dosya adının sertifikanın konu adını bulur "CN = localhost", kişisel geçerli kullanıcının depolamak ve çıkış tam dizin yolu.

```
FindPrivateKey My CurrentUser -n "CN=localhost" -a
```

Bu örnekte adla sertifikanın parmak izini bulur "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1 d 6b 52", yerel bilgisayarın kişisel deposuna.

```
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52"
```
