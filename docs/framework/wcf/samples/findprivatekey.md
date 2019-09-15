---
title: FindPrivateKey örneği-WCF
ms.date: 12/04/2017
helpviewer_keywords:
- FindPrivateKey
ms.assetid: 16b54116-0ceb-4413-af0c-753bb2a785a6
ms.openlocfilehash: 4ba4316489c1494da9421bea5c513e44c6eb50a7
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989880"
---
# <a name="findprivatekey-sample"></a>FindPrivateKey örneği

Sertifika deposundaki belirli bir X. 509.440 sertifikasıyla ilişkili özel anahtar dosyasının konumunu ve adını bulmak zor olabilir. FindPrivateKey. exe aracı bu işlemi kolaylaştırır.

> [!IMPORTANT]
> FindPrivateKey, kullanılmadan önce derlenmesi gereken bir örnektir. FindPrivateKey aracının nasıl oluşturulacağı hakkında yönergeler için bkz. [FindPrivateKey projesi oluşturmak için](#to-build-the-findprivatekey-project) bölümüne bakın.

X. 509.440 sertifikaları bir yönetici veya makinedeki herhangi bir kullanıcı tarafından yüklenir. Ancak, sertifikaya farklı bir hesap altında çalışan bir hizmet tarafından erişilebilir. Örneğin, ağ HIZMETI hesabı.

Sertifika, ilk olarak yüklenmediği için bu hesabın özel anahtar dosyasına erişimi olmayabilir. FindPrivateKey Aracı, belirli bir X. 509.440 sertifikasının özel anahtar dosyasının konumunu verir. Belirli bir X. 509.952 sertifikaları ' özel anahtar dosyasının konumunu öğrendikten sonra bu dosyaya izinler ekleyebilir veya izinleri kaldırabilirsiniz.

Güvenlik için sertifikaları kullanan örnekler *Setup. bat* dosyasındaki FindPrivateKey aracını kullanır. Özel anahtar dosyası bulduktan sonra, dosya üzerinde uygun erişim haklarını ayarlamak için *cacls. exe* gibi diğer araçları kullanabilirsiniz.

Şirket içinde barındırılan yürütülebilir dosya gibi bir kullanıcı hesabı altında bir Windows Communication Foundation (WCF) hizmeti çalıştırırken, Kullanıcı hesabının dosyaya salt okuma erişimi olduğundan emin olun. Internet Information Services (IIS) altında bir WCF Hizmeti çalıştırırken, hizmetin altında çalıştığı varsayılan hesaplar IIS 7 ve önceki sürümlerde ağ HIZMETI ya da IIS 7,5 ve sonraki sürümlerde uygulama havuzu kimliği ' nde bulunur. Daha fazla bilgi için bkz. [uygulama havuzu kimlikleri](/iis/manage/configuring-security/application-pool-identities).

## <a name="examples"></a>Örnekler

İşlemin okuma ayrıcalıklarına sahip olmadığı bir sertifikaya erişirken, aşağıdaki örneğe benzer bir özel durum iletisi görürsünüz:

```output
System.ArgumentException was unhandled
Message="The certificate 'CN=localhost' must have a private key that is capable of key exchange.  The process must have access rights for the private key."
Source="System.ServiceModel"
```

Bu durumda, özel anahtar dosyasını bulmak için FindPrivateKey aracını kullanın ve ardından hizmetin altında çalıştığı işlem için erişim hakkını ayarlayın. Örneğin, bu, aşağıdaki örnekte gösterildiği gibi cacls. exe aracı ile yapılabilir:

```console
cacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /E /G "NETWORK SERVICE":R
```

#### <a name="to-build-the-findprivatekey-project"></a>FindPrivateKey projesi oluşturmak için

Projeyi indirmek için [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerini](https://www.microsoft.com/download/details.aspx?id=21459)ziyaret edin.

1. Dosya Gezgini 'ni açın ve örneği yüklediğiniz dizin konumunun altındaki *WF_WCF_Samples\WCF\Setup\FindPrivateKey\CS* klasörüne gidin.

2. Visual Studio 'da dosyayı açmak için. sln dosya simgesine çift tıklayın.

3. **Derle** menüsünde **çözümü yeniden derle**' yi seçin.

4. Çözümü oluşturmak dosyayı oluşturur: FindPrivateKey. exe.

## <a name="conventionscommand-line-entries"></a>Kurallar — komut satırı girdileri

 "[*seçenek*]", isteğe bağlı bir parametre kümesini temsil eder.

 "{*Option*}", zorunlu bir parametre kümesini temsil eder.

 "*Seçenek1* &#124; *Seçenek2*" seçenek kümeleri arasında bir seçimi temsil eder.

 "\<*değer*>" girilecek bir parametre değeri temsil eder.

## <a name="usage"></a>Kullanım

```console
FindPrivateKey <storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]
```

Konum:

| Parametre         | Açıklama                                                                       |
|-----------------|-----------------------------------------------------------------------------------|
| `<subjectName>` | Sertifikanın konu adı                                               |
| `<thumbprint>`  | Sertifikanın parmak izi (bunu bulmak için certmgr. exe aracını kullanabilirsiniz) |
| `-f`            | yalnızca çıkış dosyası adı                                                             |
| `-d`            | yalnızca çıkış dizini                                                             |
| `-a`            | çıkış mutlak dosya adı                                                         |

Komut isteminde hiçbir parametre belirtilmemişse, bu bilgileri içeren yardım metni görüntülenir.

## <a name="examples"></a>Örnekler

Bu örnek, geçerli kullanıcının kişisel deposunda "CN = localhost" konu adına sahip sertifikanın dosya adını bulur.

```console
FindPrivateKey My CurrentUser -n "CN=localhost"
```

Bu örnek, geçerli kullanıcının kişisel deposunda "CN = localhost" konu adına sahip sertifikanın dosya adını bulur ve tam dizin yolunu çıktı olarak belirler.

```console
FindPrivateKey My CurrentUser -n "CN=localhost" -a
```

Bu örnek, yerel bilgisayarın Kişisel deposunda "03 33 98 63 D0 47 E7 48 71 33 62 64 76 5c 4c 9D 42 1D 6B 52" parmak izine sahip sertifikanın dosya adını bulur.

```console
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52"
```
