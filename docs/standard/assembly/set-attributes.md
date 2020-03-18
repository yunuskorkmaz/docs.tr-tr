---
title: Derleme özniteliklerini ayarlama
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], attributes
- assembly binding, attributes
- assembly manifest, attributes
ms.assetid: 36a98a81-b5b5-4c19-912a-11f91eff7f4e
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 0e4e2e595ed4f95511bd23ab0ed00139f71b2c8b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73740479"
---
# <a name="set-assembly-attributes"></a>Derleme özniteliklerini ayarlama

Derleme öznitelikleri, derleme hakkında bilgi sağlayan değerlerdir. Öznitelikler aşağıdaki bilgi kümelerine ayrılır:

- Montaj kimlik öznitelikleri

- Bilgilendirme özellikleri

- Derleme bildirim öznitelikleri

- Güçlü ad öznitelikleri

## <a name="assembly-identity-attributes"></a>Montaj kimlik öznitelikleri

Güçlü bir adla birlikte (varsa) üç öznitelik, bir derlemenin kimliğini belirler: ad, sürüm ve kültür. Bu öznitelikler derlemenin tam adını oluşturur ve derlemeyi kodla ifade ederken gereklidir. Derlemenin sürümünü ve kültürünü ayarlamak için öznitelikleri kullanabilirsiniz. Derleyici veya [Derleme Bağlayıcısı (Al.exe),](../../framework/tools/al-exe-assembly-linker.md) derleme bildirimini içeren dosyayı temel alınca, derleme oluşturulduğunda ad değerini ayarlar.

Aşağıdaki tabloda sürüm ve kültür öznitelikleri açıklanmaktadır.

|Derleme kimlik özniteliği|Açıklama|
|---------------------------------|-----------------|
|<xref:System.Reflection.AssemblyCultureAttribute>|Derlemenin desteklediği kültürü gösteren numaralandırılmış alan. Bir derleme, varsayılan kültür için kaynakları içerdiğini belirterek kültür bağımsızlığını da belirtebilir. **Not:**  Çalışma zamanı, uydu derlemesi olarak null olarak ayarlanmış kültür özniteliği olmayan herhangi bir derlemeyi davranır. Bu tür derlemeler uydu montaj bağlama kurallarına tabidir. Daha fazla bilgi için [çalışma zamanının derlemeleri nasıl bulabildiğini](../../framework/deployment/how-the-runtime-locates-assemblies.md)görün.|
|<xref:System.Reflection.AssemblyFlagsAttribute>|Derlemenin yan yana çalıştırılıp çalıştırılamayacağı gibi derleme özniteliklerini ayarlayan değer.|
|<xref:System.Reflection.AssemblyVersionAttribute>|Biçim *ana'daki*sayısal değer. *küçük*. *inşa edin.* *revizyon* (örneğin, 2.4.0.0). Ortak dil çalışma süresi, bağlı adlandırılmış derlemelerde bağlama işlemleri gerçekleştirmek için bu değeri kullanır. **Not:**  Öznitelik <xref:System.Reflection.AssemblyInformationalVersionAttribute> bir derlemeye uygulanmazsa, öznitelik <xref:System.Reflection.AssemblyVersionAttribute> tarafından belirtilen sürüm numarası <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType>, <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType>, <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType> ve özellikleri tarafından kullanılır.|

Aşağıdaki kod örneği, sürüm ve kültür özniteliklerinin bir derlemeye nasıl uygulanacağı gösterilmektedir.

```cpp
// Set version number for the assembly.
[assembly:AssemblyVersionAttribute("4.3.2.1")];
// Set culture as German.
[assembly:AssemblyCultureAttribute("de")];
```

```csharp
// Set version number for the assembly.
[assembly:AssemblyVersionAttribute("4.3.2.1")]
// Set culture as German.
[assembly:AssemblyCultureAttribute("de")]
```

```vb
' Set version number for the assembly.
<Assembly:AssemblyVersionAttribute("4.3.2.1")>
' Set culture as German.
<Assembly:AssemblyCultureAttribute("de")>
```

## <a name="informational-attributes"></a>Bilgilendirme özellikleri

Bir derleme için ek şirket veya ürün bilgileri sağlamak için bilgi özniteliklerini kullanabilirsiniz. Aşağıdaki tabloda, bir derlemeye uygulayabileceğiniz bilgi öznitelikleri açıklanmaktadır.

|Bilgilendirme özniteliği|Açıklama|
|-----------------------------|-----------------|
|<xref:System.Reflection.AssemblyCompanyAttribute>|Şirket adını belirten dize değeri.|
|<xref:System.Reflection.AssemblyCopyrightAttribute>|Telif hakkı bilgilerini belirten dize değeri.|
|<xref:System.Reflection.AssemblyFileVersionAttribute>|Win32 dosya sürüm numarasını belirten dize değeri. Bu normalde varsayılan olarak derleme sürümüne bağlıdır.|
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|Tam ürün sürüm numarası gibi ortak dil çalışma zamanı tarafından kullanılmayan sürüm bilgilerini belirten dize değeri. **Not:**  Bu öznitelik bir derlemeye uygulanırsa, belirttiği dize <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType> özelliği kullanılarak çalışma zamanında elde edilebilir. Dize, yol ve kayıt defteri anahtarında <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType> <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType> da kullanılır.|
|<xref:System.Reflection.AssemblyProductAttribute>|Ürün bilgilerini belirten dize değeri.|
|<xref:System.Reflection.AssemblyTrademarkAttribute>|Ticari marka bilgilerini belirten dize değeri.|

Bu öznitelikler derlemenin Windows Properties sayfasında görünebilir veya kendi Win32 kaynak dosyanızı belirtmek için **/win32res** derleyicisi seçeneğini kullanarak geçersiz kılınabilir.

## <a name="assembly-manifest-attributes"></a>Derleme bildirim öznitelikleri

Başlık, açıklama, varsayılan takma ad ve yapılandırma gibi derleme bildiriminde bilgi sağlamak için derleme bildirimi özniteliklerini kullanabilirsiniz. Aşağıdaki tabloda derleme bildirimi öznitelikleri açıklanmaktadır.

|Derleme bildirim özniteliği|Açıklama|
|---------------------------------|-----------------|
|<xref:System.Reflection.AssemblyConfigurationAttribute>|Perakende veya Hata Ayıklama gibi derlemeyapılandırmasını gösteren dize değeri. Çalışma süresi bu değeri kullanmaz.|
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|Derlemelere başvurarak kullanılacak varsayılan bir diğer adı belirten dize değeri. Bu değer, derlemenin adı uygun olmadığında (GUID değeri gibi) dostça bir ad sağlar. Bu değer, tam montaj adının kısa bir biçimi olarak da kullanılabilir.|
|<xref:System.Reflection.AssemblyDescriptionAttribute>|Derlemenin niteliğini ve amacını özetleyen kısa bir açıklama belirten dize değeri.|
|<xref:System.Reflection.AssemblyTitleAttribute>|Montaj için uygun bir ad belirten dize değeri. Örneğin, *comdlg* adlı bir derleme microsoft ortak iletişim denetimi başlığına sahip olabilir.|

## <a name="strong-name-attributes"></a>Güçlü ad öznitelikleri

Derleme için güçlü bir ad ayarlamak için güçlü ad öznitelikleri kullanabilirsiniz. Aşağıdaki tabloda güçlü ad öznitelikleri açıklanmaktadır.

|Güçlü ad özniteliği|Açıklama|
|----------------------------|-----------------|
|<xref:System.Reflection.AssemblyDelaySignAttribute>|Gecikme imzalamanın kullanıldığını belirten boolean değeri.|
|<xref:System.Reflection.AssemblyKeyFileAttribute>|Ortak anahtarı (gecikme imzalamayı kullanıyorsanız) veya bu özniteliğin oluşturucuya parametre olarak aktarılan ortak ve özel anahtarları içeren dosyanın adını gösteren dize değeri. Dosya adının kaynak dosya yolu ile değil, çıktı dosyası yoluna *(.exe* veya *.dll)* göreli olduğunu unutmayın.|
|<xref:System.Reflection.AssemblyKeyNameAttribute>|Bu özniteliğin oluşturucuya parametre olarak geçirilen anahtar çiftini içeren anahtar kapsayıcısını gösterir.|

Aşağıdaki kod örneği, *myKey.snk*adlı ortak anahtar dosyası içeren güçlü bir anahtar dosyası oluşturmak için gecikme imzalamayı kullanırken uygulanacak öznitelikleri gösterir.

```cpp
[assembly:AssemblyKeyFileAttribute("myKey.snk")];
[assembly:AssemblyDelaySignAttribute(true)];
```

```csharp
[assembly:AssemblyKeyFileAttribute("myKey.snk")]
[assembly:AssemblyDelaySignAttribute(true)]
```

```vb
<Assembly:AssemblyKeyFileAttribute("myKey.snk")>
<Assembly:AssemblyDelaySignAttribute(True)>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Derleme oluşturma](create.md)
