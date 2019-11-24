---
title: Mage.exe (Bildirim Üretme ve Düzenleme Aracı)
ms.date: 12/06/2018
helpviewer_keywords:
- Manifest Generation and Editing tool
- Mage.exe
ms.assetid: 77dfe576-2962-407e-af13-82255df725a1
ms.openlocfilehash: aa2ad9222460f8732397f8b1c72e36085bbe4a21
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449426"
---
# <a name="mageexe-manifest-generation-and-editing-tool"></a>Mage.exe (Bildirim Üretme ve Düzenleme Aracı)

The Manifest Generation and Editing Tool (*Mage.exe*) is a command-line tool that supports the creation and editing of application and deployment manifests. As a command-line tool, *Mage.exe* can be run from both batch scripts and other Windows-based applications, including ASP.NET applications.

You can also use *MageUI.exe*, a graphical application, instead of *Mage.exe*. For more information, see [MageUI.exe (Manifest Generation and Editing Tool, Graphical Client)](mageui-exe-manifest-generation-and-editing-tool-graphical-client.md).

Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. To run the tool, use Developer Command Prompt for Visual Studio. For more information, see [Command Prompts](developer-command-prompt-for-vs.md).

Two versions of *Mage.exe* and *MageUI.exe* are included with Visual Studio. To see version information, run *MageUI.exe*, select **Help**, and select **About**. This documentation describes version 4.0.x.x of *Mage.exe* and *MageUI.exe*.

## <a name="syntax"></a>Sözdizimi

```console
Mage [commands] [commandOptions]
```

## <a name="parameters"></a>Parametreler

The following table shows the commands supported by *Mage.exe*. For more information about the options supported by these commands, see [New and Update command options](#new-and-update-command-options) and [Sign command options](#sign-command-options).

|Komut|Açıklama|
|-------------|-----------------|
|**-cc, ClearApplicationCache**|Tüm yalnızca çevrimiçi uygulamalar için indirilen uygulama önbelleğini temizler.|
|**-n, -New** *fileType [newOptions]*|Belirtilen türde yeni bir dosya oluşturur. Geçerli türler şunlardır:<br /><br /> -   `Deployment`: Creates a new deployment manifest.<br />-   `Application`: Creates a new application manifest.<br /><br /> Eğer bu komutla birlikte hiçbir ek parametre belirtmezseniz, uygun türde ve uygun varsayılan etiketlere ve öznitelik değerlerine sahip bir dosya oluşturur.<br /><br /> Use the **-ToFile** option (see in the following table) to specify the file name and path of the new file.<br /><br /> Use the **-FromDirectory** option (see in the following table) to create an application manifest with all of the assemblies for an application added to the \<dependency> section of the manifest.|
|**-u, -Update** *[filePath] [updateOptions]*|Bir bildirim dosyasına bir veya daha fazla değişiklik yapar. Düzenlediğiniz dosya türünü belirtmeniz gerekli değildir. Mage.exe, bir buluşsal yöntem kümesi kullanarak dosyayı inceler ve bir dağıtım bildirimi ya da uygulama bildirimi olup olmadığını belirler.<br /><br /> If you have already signed a file with a certificate, **-Update** will remove the key signature block. Bunun nedeni, anahtar imzasının dosyasının bir karmasını içermesi ve dosyayı değiştirmenin karmayı geçersiz kılmasıdır.<br /><br /> Use the **-ToFile** option (see in the following table) to specify a new file name and path instead of overwriting the existing file.|
|**-s, -Sign** `[signOptions]`|Bir dosyayı imzalamak için bir anahtar çifti veya X509 sertifikası kullanır. İmzalar, dosyaların içine XML öğeleri olarak eklenir.<br /><br /> You must be connected to the Internet when signing a manifest that specifies a **-TimestampUri** value.|
|**-ver, -Verify** *[manifest-filename]*|Verifies that the manifest is signed correctly. Cannot be combined with other commands. <br/><br/>**Available in .NET Framework 4.7 and later versions.**|
|**-h, -?, -Help** *[verbose]*|Tüm kullanılabilir komutları ve seçeneklerini açıklar. Specify `verbose` to get detailed help.|

## <a name="new-and-update-command-options"></a>New and Update command options

The following table shows the options supported by the `-New` and `-Update` commands:

|Seçenekler|Varsayılan Değer|Uygulanan Öğe|Açıklama|
|-------------|-------------------|----------------|-----------------|
|**-a, -Algorithm**|sha1RSA|Uygulama bildirimleri.<br /><br /> Dağıtım bildirimleri.|Bağımlılık özetlerinin oluşturması için kullanılan algoritmayı belirtir. Değer "sha256RSA" veya "sha1RSA" olmalıdır.<br /><br /> "-Update" seçeneğiyle kullanın. Bu seçenek "-Sign" seçeneğini kullanırken yok sayılır.|
|**-appc, -AppCodeBase** `manifestReference`||Dağıtım bildirimleri.|Uygulama bildirim dosyasına bir URL veya dosya yolu başvurusu ekler. Bu değer, uygulama bildiriminin tam yolu olmalıdır.|
|**-appm, -AppManifest** `manifestPath`||Dağıtım bildirimleri.|Bir dağıtım bildirimine, dağıtımın uygulama bildirimindeki bir başvuruyu ekler.<br /><br /> The file indicated by `manifestPath` must exist, or *Mage.exe* will issue an error. If the file referenced by `manifestPath` is not an application manifest, *Mage.exe* will issue an error.|
|**-cf, -CertFile** `filePath`||Tüm dosya türleri.|Specifies the location of an X509 digital certificate for signing a manifest or license file. This option can be used in conjunction with the **-Password** option if the certificate requires a password for Personal Information Exchange (PFX) files. Starting with .NET Framework 4.7, if the file does not contain a private key, a combination of the **-CryptoProvider** and **-KeyContainer** options is required.<br/><br/>Starting with .NET Framework 4.6.2, *Mage.exe* signs manifests with CNG as well as CAPI certificates.|
|**-ch, -CertHash** `hashSignature`||Tüm dosya türleri.|İstemci bilgisayarın kişisel sertifika deposunda tutulan bir dijital sertifikanın karması. Bu, Windows Sertifikaları Konsolu içinde görüntülenen bir dijital sertifikanın Parmak İzi dizesine karşılık gelir.<br /><br /> `hashSignature` can be either uppercase or lowercase, and can be supplied either as a single string, or with each octet of the Thumbprint separated by spaces and the entire Thumbprint enclosed in quotation marks.|
|**-csp, -CryptoProvider** `provider-name`||Tüm dosya türleri.|Specifies the name of a cryptographic service provider (CSP) that contains the private key container. This option requires the **-KeyContainer** option.<br/><br/>This option is available starting with .NET Framework 4.7.|
|**-fd, -FromDirectory** `directoryPath`||Uygulama bildirimleri.|Populates the application manifest with descriptions of all assemblies and files found in `directoryPath`, including all subdirectories, where `directoryPath` is the directory that contains the application that you want to deploy. For each file in the directory, *Mage.exe* decides whether the file is an assembly or a static file. If it is an assembly, it adds a `<dependency>` tag and `installFrom` attribute to the application with the assembly's name, code base, and version. If it is a static file, it adds a `<file>` tag. *Mage.exe* will also use a simple set of heuristics to detect the main executable for the application, and will mark it as the ClickOnce application's entry point in the manifest.<br /><br /> *Mage.exe* will never automatically mark a file as a "data" file. Bunu elle yapmanız gerekir. For more information, see [How to: Include a Data File in a ClickOnce Application](/visualstudio/deployment/how-to-include-a-data-file-in-a-clickonce-application).<br /><br /> *Mage.exe* also generates a hash for each file based on its size. ClickOnce bu karmaları kullanarak, bildirim oluşturulduktan sonra dağıtımın dosyaları üzerinde kimsenin değişiklik yapmadığından emin olur. If any of the files in your deployment change, you can run *Mage.exe* with the **-Update** command and the **-FromDirectory** option, and it will update the hashes and assembly versions of all referenced files.<br /><br /> **-FromDirectory** will include all files in all subdirectories found within `directoryPath`.<br /><br /> If you use **-FromDirectory** with the **-Update** command, *Mage.exe* will remove any files in the application manifest that no longer exist in the directory.|
|**-if, -IconFile**  `filePath`||Uygulama bildirimleri.|Bir .ICO simge dosyasının tam yolunu belirtir. Bu simge başlat menüsünde uygulamanızın adının yanında ve Program Ekle/Kaldır girdisinde görünür. Eğer simge sağlanmazsa, varsayılan bir simge kullanılır.|
|**-ip, -IncludeProviderURL**  `url`|true|Dağıtım bildirimleri.|Indicates whether the deployment manifest includes the update location value set by **-ProviderURL**.|
|**-i, -Install** `willInstall`|true|Dağıtım bildirimleri.|ClickOnce uygulamasının yerel bilgisayara yüklenip yüklenmeyeceğini veya Web'den çalışıp çalışmayacağını belirtir. Installing an application gives that application a presence in the Windows **Start** menu. Geçerli değerler "true" veya "t" ve "false" veya "f" değerleridir.<br /><br /> If you specify the **-MinVersion** option, and a user has a version less than **-MinVersion** installed, it will force the application to install, regardless of the value that you pass to **-Install**.<br /><br /> This option cannot be used with the **-BrowserHosted** option. Aynı bildirimde ikisini de belirtmeyi denemek hata oluşturur.|
|**-kc, -KeyContainer** `name`||Tüm dosya türleri.|Specifies the key container that contains the name of the private key. This option requires the **CryptoProvider** option.<br/><br/>This option is available starting with .NET Framework 4.7.|
|**-mv, -MinVersion**  `[version]`|The version listed in the ClickOnce deployment manifest as specified by the **-Version** flag.|Dağıtım bildirimleri.|Bir kullanıcının çalıştırabileceği bu uygulamanın en düşük sürümü. Bu bayrak uygulamanızın adlandırılmış sürümünü gereken bir güncelleştirme yapar. Eğer ürününüzün bir sürümünü bozucu bir değişiklik veya kritik bir güvenlik açığı için güncelleştirirseniz, bu bayrağı kullanarak bu güncelleştirmenin yüklenmesi gerektiğini ve kullanıcının önceki sürümleri kullanamayacağını belirtebilirsiniz.<br /><br /> `version` has the same semantics as the argument to the **-Version** flag.|
|**-n, -Name** `nameString`|Dağıt|Tüm dosya türleri.|Uygulamayı tanımlamak için kullanılan ad. ClickOnce will use this name to identify the application in the **Start** menu (if the application is configured to install itself) and in Permission Elevation dialog boxes. **Note:**  If you are updating an existing manifest and you do not specify a publisher name with this option, *Mage.exe* updates the manifest with the organization name defined on the computer. Farklı bir ad kullanmak için, bu seçeneği kullanmayı ve istediğiniz yayımcı adını belirtmeyi unutmayın.|
|**-pwd, -Password** `passwd`||Tüm dosya türleri.|Bir bildirimi dijital sertifika ile imzalamak için kullanılan şifre. Must be used in conjunction with the **-CertFile** option.|
|**-p, Processor** `processorValue`|Msil|Uygulama bildirimleri.<br /><br /> Dağıtım bildirimleri.|Bu dağıtımın çalışabileceği mikro işlemci mimarisi. Eğer derlemeleri belirli bir mikro işlemci için önceden derlenmiş olan bir veya daha fazla yükleme için hazırlanıyorsanız bu değer gereklidir. Valid values include `msil`, `x86`, `ia64`, and `amd64`. `msil` is Microsoft intermediate language, which means all of your assemblies are platform-independent, and the common language runtime (CLR) will just-in-time compile them when your application is first run.|
|**-pu,** **-ProviderURL** `url`||Dağıtım bildirimleri.|ClickOnce'ın uygulama güncelleştirmeleri için inceleyeceği URL'yi belirtir.|
|**-pub, -Publisher** `publisherName`||Uygulama bildirimleri.<br /><br /> Dağıtım bildirimleri.|Dağıtım veya uygulama bildiriminin açıklama öğesine yayımcı adını ekler. When used on an application manifest, **-UseManifestForTrust** must also be specified with a value of "true" or "t"; otherwise, this parameter will raise an error.|
|**-s, -SupportURL**  `url`||Uygulama bildirimleri.<br /><br /> Dağıtım bildirimleri.|ClickOnce uygulaması için Program Ekle veya Kaldır'da görünen bağlantıyı belirtir.|
|**-ti, -TimestampUri** `uri`||Uygulama bildirimleri.<br /><br /> Dağıtım bildirimleri.|Bir dijital zaman damgası hizmetinin URL'si. Bildirimlere zaman damgası koymak, uygulamanızın sonraki sürümünü dağıtmadan önce dijital sertifikanızın süresi dolarsa bildirimleri yeniden imzalamanıza gerek kalmamasını sağlar. For more information, see [Windows root certificate program members](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn265983(v=ws.11)).|
|**-t, -ToFile** `filePath`|-   New:<br />-   Deployment: deploy.application<br />-   Application: application.exe.manifest<br />-   Update:<br />-   The input file.|Tüm dosya türleri.|Oluşturulan veya değiştirilen dosyanın çıkış yolunu belirtir.<br /><br /> If **-ToFile** is not supplied when you use **-New**, the output is written to the current working directory. If **-ToFile** is not supplied when you use **-Update**, *Mage.exe* will write the file back to the input file.|
|**-tr, -TrustLevel** `level`|Uygulama URL'sinin bulunduğu bölgeyi temel alır.|Uygulama bildirimleri.|İstemci bilgisayarlarda uygulamaya sağlanacak güven düzeyi. Değerler "Internet", "Intranet" ve "FullTrust" değerlerini içerir.|
|**-um, -UseManifestForTrust** `willUseForTrust`|False|Uygulama bildirimleri.|Uygulama bildiriminin dijital imzasının, uygulama istemcide çalışırken güven kararları için kullanılıp kullanılmayacağını belirtir. "true" veya "t" belirtmek uygulama bildiriminin güven kararları için kullanılacağını belirtir. "false" veya "f" belirtmek dağıtım bildiriminin imzasının kullanılacağını belirtir.|
|**-v, -Version** `versionNumber`|1.0.0.0|Uygulama bildirimleri.<br /><br /> Dağıtım bildirimleri.|Dağıtımın sürümü. The argument must be a valid version string of the format "*N.N.N.N*", where "*N*" is an unsigned 32-bit integer.|
|**-wpf, -WPFBrowserApp**  `isWPFApp`|false|Uygulama bildirimleri.<br /><br /> Dağıtım bildirimleri.|Bu bayrağı yalnızca, uygulama Internet Explorer içinde barındırılacak bir Windows Presentation Foundation (WPF) uygulaması ise ve tek başına yürütülebilir dosya değil ise kullanın. Geçerli değerler "true" veya "t" ve "false" veya "f" değerleridir.<br /><br /> For application manifests, inserts the `hostInBrowser` attribute under the `entryPoint` element of the application manifest.<br /><br /> For deployment manifests, sets the `install` attribute on the `deployment` element to false, and saves the deployment manifest with a .xbap extension. Specifying this argument along with the **-Install** argument produces an error, because a browser-hosted application cannot be an installed, offline application.|

## <a name="sign-command-options"></a>Sign command options

The following table shows the options supported by the `-Sign` command, which apply to all types of files.

|Seçenekler|Açıklama|
|-------------|-----------------|
|**-cf, -CertFile** `filePath`|Bildirim imzalamak için bir dijital sertifikanın konumunu belirtir. This option can be used in conjunction with the **-Password** option if the certificate requires a password for Personal Information Exchange (PFX) files. Starting with .NET Framework 4.7, if the file does not contain a private key, a combination of the **-CryptoProvider** and **-KeyContainer** options is required.<br/><br/>Starting with .NET Framework 4.6.2, *Mage.exe* signs manifests with CNG as well as CAPI certificates.|
|**-ch, -CertHash** `hashSignature`|İstemci bilgisayarın kişisel sertifika deposunda tutulan bir dijital sertifikanın karması. Bu, Windows Sertifikaları Konsolu içinde görüntülenen bir dijital sertifikanın Parmak İzi özelliğine karşılık gelir.<br /><br /> `hashSignature` can be either uppercase or lowercase, and can be supplied either as a single string or with each octet of the Thumbprint separated by spaces and the entire Thumbprint enclosed in quotation marks.|
**-csp, -CryptoProvider** `provider-name`|Specifies the name of a cryptographic service provider (CSP) that contains the private key container. This option requires the **-KeyContainer** option.<br/><br/>This option is available starting with .NET Framework 4.7.|
|**-kc, -KeyContainer** `name`|Specifies the key container that contains the name of the private key. This option requires the **CryptoProvider** option.<br/><br/>This option is available starting with .NET Framework 4.7.|
|**-pwd, -Password** `passwd`|Bir bildirimi dijital sertifika ile imzalamak için kullanılan şifre. Must be used in conjunction with the **-CertFile** option.|
|**-t, -ToFile** `filePath`|Oluşturulan veya değiştirilen dosyanın çıkış yolunu belirtir.|

## <a name="remarks"></a>Açıklamalar

All arguments to *Mage.exe* are case-insensitive. Komutlar ve seçenekler bir tire (-) veya eğik çizgi (/) ile belirtilebilir.

All of the arguments used with the **-Sign** command can be used at any time with the **-New** or **-Update** commands as well. Aşağıdaki komutlar eşdeğerdir.

```console
mage -Sign c:\HelloWorldDeployment\HelloWorld.deploy -CertFile cert.pfx
mage -Update c:\HelloWorldDeployment\HelloWorld.deploy -CertFile cert.pfx
```

> [!NOTE]
> Beginning with .NET Framework version 4.6.2, CNG certificates are also supported.

 İmzalama gerçekleştireceğiniz son görevdir; çünkü imzalanmış bir belge, imzanın belge için geçerli olup olmadığını doğrulamak için dosyanın bir karmasını kullanır. Eğer imzalanan dosyada bir değişiklik yaparsanız, yeniden imzalamanız gerekir. If you sign a document that was previously signed, *Mage.exe* will replace the old signature with the new.

 When you use the **-AppManifest** option to populate a deployment manifest, *Mage.exe* will assume that your application manifest will reside in the same directory as the deployment manifest within a subdirectory named after the current deployment version, and will configure your deployment manifest appropriately. If your application manifest will reside elsewhere, use the **-AppCodeBase** option to set the alternate location.

 Uygulamanızı dağıtmadan önce dağıtım ve uygulama belgeleriniz imzalanmalıdır. For guidance about signing manifests, see [Trusted Application Deployment Overview](/visualstudio/deployment/trusted-application-deployment-overview).

 The **-TrustLevel** option for application manifests describes the permission set an application requires to run on the client computer. By default, applications are assigned a trust level based on the *zone* in which their URL resides. Bir şirket ağında dağıtılan uygulamalar genellikle Intranet bölgesine yerleştirilirken, Internet üzerinden dağıtılan uygulamalar Internet bölgesine yerleştirilir. İki güvenlik bölgesi de uygulamanın yerel kaynaklara erişimine kısıtlamalar koyar, ancak Intranet bölgesi Internet bölgesine göre biraz daha az sınırlayıcıdır. FullTrust bölgesi uygulamalara, bir bilgisayarın yerel kaynakları için tam erişim sağlar. If you use the **-TrustLevel** option to place an application in this zone, the Trust Manager component of the CLR will prompt the user to decide whether he or she wants to grant this higher level of trust. Eğer uygulamanızı bir şirket ağı üzerinden dağıtıyorsanız, kullanıcıya sormadan uygulamanın güven düzeyini yükseltmek için Güvenilen Uygulama Dağıtımı'nı kullanabilirsiniz.

 Uygulama bildirimleri de özel güven bölümlerini destekler. Bu, uygulamanızın en az izni isteme güvenlik ilkesine uymasına yardımcı olur; çünkü bildirimi, uygulamanın yürütülebilmesi için gereken belirli izinleri isteyecek şekilde yapılandırabilirsiniz. *Mage.exe* does not directly support adding a custom trust section. You can add one using a text editor, an XML parser, or the graphical tool *MageUI.exe*. For more information about how to use *MageUI.exe* to add custom trust sections, see [MageUI.exe (Manifest Generation and Editing Tool, Graphical Client)](mageui-exe-manifest-generation-and-editing-tool-graphical-client.md).

Visual Studio 2017 includes version 4.6.1 of *Mage.exe*. Manifests created with this version of *Mage.exe* target .NET Framework 4. To target older versions of the .NET Framework, use an earlier version of *Mage.exe*.

When you add or remove assemblies from an existing manifest, or re-sign an existing manifest, *Mage.exe* does not update the manifest to target .NET Framework 4.

The following tables show these features and restrictions:

|Bildirim sürümü|Çalışma|Mage v2.0|Mage v4.0|
|----------------------|---------------|---------------|---------------|
|.NET Framework'ün 2.0 veya 3.x sürümünü hedefleyen uygulamalar için bildirim|Open|Tamam|Tamam|
||Close|Tamam|Tamam|
||Kaydet|Tamam|Tamam|
||Yeniden İmzala|Tamam|Tamam|
||Yeni|Tamam|Desteklenmez|
||Update (aşağıya bakın)|Tamam|Tamam|
|.NET Framework'ün 4 sürümünü hedefleyen uygulamalar için bildirim|Open|Tamam|Tamam|
||Close|Tamam|Tamam|
||Kaydet|Tamam|Tamam|
||Yeniden İmzala|Tamam|Tamam|
||Yeni|Desteklenmez|Tamam|
||Update (aşağıya bakın)|Desteklenmez|Tamam|

|Bildirim sürümü|Update İşlemi Ayrıntıları|Mage v2.0|Mage v4.0|
|----------------------|------------------------------|---------------|---------------|
|.NET Framework'ün 2.0 veya 3.x sürümünü hedefleyen uygulamalar için bildirim|Bir derlemeyi değiştir|Tamam|Tamam|
||Bir derleme ekle|Tamam|Tamam|
||Bir derlemeyi kaldır|Tamam|Tamam|
|.NET Framework'ün 4 sürümünü hedefleyen uygulamalar için bildirim|Bir derlemeyi değiştir|Desteklenmez|Tamam|
||Bir derleme ekle|Desteklenmez|Tamam|
||Bir derlemeyi kaldır|Desteklenmez|Tamam|

 Mage.exe creates new manifests that target the [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)]. ClickOnce applications that target the [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)] can run on both the [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)] and the full version of the .NET Framework 4. If your application targets the full version of the .NET Framework 4 and cannot run on the [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)], remove the client `<framework>` element by using a text editor and re-sign the manifest.

The following is a sample `<framework>` element that targets the [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)]:

```xml
<framework targetVersion="4.0" profile="client" supportedRuntime="4.0.20506" />
```

## <a name="examples"></a>Örnekler

The following example opens the user interface for Mage (*MageUI.exe*).

```console
mage
```

Aşağıdaki örnekler varsayılan bir dağıtım bildirimi ve uygulama bildirimi oluşturur. Bu dosyaların hepsi geçerli çalışma dizininde oluşturulur ve sırasıyla deploy.application ve application.exe.manifest olarak adlandırılır.

```console
mage -New Deployment
mage -New Application
```

The following example creates an application manifest populated with all of the assemblies and resource files from the current directory.

```console
mage -New Application -FromDirectory . -Version 1.0.0.0
```

Aşağıdaki örnek önceki örneği devam ettirerek dağıtım adımı ve hedef mikro işlemciyi belirtir. Ayrıca ClickOnce'ın güncelleştirmeler için denetleyeceği bir URL belirtir.

```console
mage -New Application -FromDirectory . -Name "Hello, World! Application" -Version 1.0.0.0 -Processor "x86" -ProviderUrl http://internalserver/HelloWorld/
```

Aşağıdaki örnek, Internet Explorer'da barındırılacak bir WPF uygulamasını dağıtmak için bir bildirim çiftinin nasıl oluşturulacağını gösterir.

```console
mage -New Application -FromDirectory . -Version 1.0.0.0 -WPFBrowserApp true
mage -New Deployment -AppManifest 1.0.0.0\application.manifest -WPFBrowserApp true
```

The following example creates an application manifest populated with all of the assemblies and resource files from the current directory and signs.

```console
mage -New Application -FromDirectory . -Version 1.0.0.0 -KeyContainer keypair.snk -CryptoProvider "Microsoft Enhanced Cryptographic Provider v1.0"
```

Aşağıdaki örnek dağıtım bildirimini bir uygulama bildirimindeki bilgiyle güncelleştirir, ve uygulama bildiriminin konumu için kod temelini ayarlar.

```console
mage -Update HelloWorld.deploy -AppManifest 1.0.0.0\application.manifest -AppCodeBase http://internalserver/HelloWorld.deploy
```

Aşağıdaki örnek dağıtım bildirimini düzenleyerek kullanıcının yüklü sürümünün zorla güncelleştirilmesini sağlar.

```console
mage -Update c:\HelloWorldDeployment\HelloWorld.deploy -MinVersion 1.1.0.0
```

Aşağıdaki örnek dağıtım bildiriminin uygulama bildirimini ayrı bir dizinden almasını sağlar.

```console
mage -Update HelloWorld.deploy -AppCodeBase http://anotherserver/HelloWorld/1.1.0.0/
```

Aşağıdaki örnek geçerli çalışma dizinindeki bir dijital sertifikayı kullanarak varolan bir dağıtım bildirimini imzalar.

```console
mage -Sign deploy.application -CertFile cert.pfx -Password <passwd>
```

The following example signs an existing deployment manifest using a digital certificate and private key in the current working directory.

```console
mage -Sign deploy.application -CertFile cert.pfx -KeyContainer keyfile.snk -CryptoProvider "Microsoft Enhanced Cryptographic Provider v1.0"
```

## <a name="see-also"></a>Ayrıca bkz.

- [ClickOnce Güvenliği ve Dağıtımı](/visualstudio/deployment/clickonce-security-and-deployment)
- [İzlenecek yol: ClickOnce Uygulamasını El ile Dağıtma](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)
- [Güvenilir Uygulama Dağıtımına Genel Bakış](/visualstudio/deployment/trusted-application-deployment-overview)
- [MageUI.exe (Bildirim Oluşturma ve Düzenleme Aracı, Grafik İstemci)](mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)
- [Komut İstemleri](developer-command-prompt-for-vs.md)
