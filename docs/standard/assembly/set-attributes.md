---
title: Derleme özniteliklerini ayarla
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], attributes
- assembly binding, attributes
- assembly manifest, attributes
ms.assetid: 36a98a81-b5b5-4c19-912a-11f91eff7f4e
author: rpetrusha
ms.author: ronpet
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: d0809ec3da5a12abe950e63f9665037323a0ab39
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991675"
---
# <a name="set-assembly-attributes"></a>Derleme özniteliklerini ayarla

Derleme öznitelikleri, bir derleme hakkında bilgi sağlayan değerlerdir. Öznitelikler aşağıdaki bilgi kümelerine ayrılır:

- Bütünleştirilmiş kod kimliği öznitelikleri

- Bilgilendirici öznitelikler

- Bütünleştirilmiş kod bildirim öznitelikleri

- Tanımlayıcı ad öznitelikleri

## <a name="assembly-identity-attributes"></a>Bütünleştirilmiş kod kimliği öznitelikleri

Bir tanımlayıcı ad (varsa) ile birlikte üç öznitelik, bir derlemenin kimliğini belirleme: ad, sürüm ve kültür. Bu öznitelikler, derlemenin tam adını oluşturur ve koddaki derlemeye başvurulduğunda gereklidir. Öznitelikleri, bir derlemenin sürümünü ve kültürünü ayarlamak için kullanabilirsiniz. Derleyici veya [derleme Bağlayıcısı (al. exe)](../../framework/tools/al-exe-assembly-linker.md) , derleme bildirimini içeren dosyaya bağlı olarak, derleme oluşturulduğunda ad değerini ayarlar.

Aşağıdaki tabloda sürüm ve kültür öznitelikleri açıklanmaktadır.

|Bütünleştirilmiş kod kimliği özniteliği|Açıklama|
|---------------------------------|-----------------|
|<xref:System.Reflection.AssemblyCultureAttribute>|Derlemenin desteklediği kültürü gösteren numaralandırılmış alan. Bir bütünleştirilmiş kod ayrıca kültür bağımsızlığını belirtebilir ve bu, varsayılan kültürün kaynaklarını içerdiğini belirtir. **Not:**  Çalışma zamanı, kültür özniteliği olmayan herhangi bir derlemeyi uydu derlemesi olarak null olarak ayarlanmış şekilde değerlendirir. Bu tür derlemeler uydu derleme bağlama kurallarına tabidir. Daha fazla bilgi için bkz. [çalışma zamanı derlemeleri nasıl konumlandırır](../../framework/deployment/how-the-runtime-locates-assemblies.md).|
|<xref:System.Reflection.AssemblyFlagsAttribute>|Derlemenin yan yana çalıştırılıp çalıştırılmayacağı gibi, derleme özniteliklerini ayarlayan değer.|
|<xref:System.Reflection.AssemblyVersionAttribute>|*Birincil*biçimdeki sayısal değer. *küçük*. *oluşturun*. *Düzeltme* (örneğin, 2.4.0.0). Ortak dil çalışma zamanı, tanımlayıcı adlı derlemelerde bağlama işlemleri gerçekleştirmek için bu değeri kullanır. **Not:**  <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType> <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType> <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType> Özniteliği bir derlemeye uygulanmadığından, <xref:System.Reflection.AssemblyVersionAttribute> özniteliği tarafından belirtilen sürüm numarası,, ve özellikleri tarafından kullanılır. <xref:System.Reflection.AssemblyInformationalVersionAttribute>|

Aşağıdaki kod örneği, bir derlemeye sürüm ve kültür özniteliklerinin nasıl uygulanacağını gösterir.

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

## <a name="informational-attributes"></a>Bilgilendirici öznitelikler

Bir derlemeye ek şirket veya ürün bilgileri sağlamak için bilgilendirici öznitelikleri kullanabilirsiniz. Aşağıdaki tabloda, bir derlemeye uygulayabileceğiniz bilgilendirici öznitelikler açıklanmaktadır.

|Bilgilendirici özniteliği|Açıklama|
|-----------------------------|-----------------|
|<xref:System.Reflection.AssemblyCompanyAttribute>|Şirket adını belirten dize değeri.|
|<xref:System.Reflection.AssemblyCopyrightAttribute>|Telif hakkı bilgilerini belirten dize değeri.|
|<xref:System.Reflection.AssemblyFileVersionAttribute>|Win32 dosya sürümü numarasını belirten dize değeri. Bu, normalde derleme sürümünü varsayılan olarak belirler.|
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|Tam ürün sürümü numarası gibi ortak dil çalışma zamanı tarafından kullanılmayan sürüm bilgilerini belirten dize değeri. **Not:**  Bu öznitelik bir derlemeye uygulanırsa, belirttiği dize <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType> özelliği kullanılarak çalışma zamanında elde edilebilir. Dize, <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType> ve <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType> özellikleri tarafından sunulan yol ve kayıt defteri anahtarında de kullanılır.|
|<xref:System.Reflection.AssemblyProductAttribute>|Ürün bilgilerini belirten dize değeri.|
|<xref:System.Reflection.AssemblyTrademarkAttribute>|Ticari marka bilgilerini belirten dize değeri.|

Bu öznitelikler, derlemenin Windows özellikleri sayfasında görünebilir veya kendi Win32 kaynak dosyanızı belirtmek için **/win32res** derleyici seçeneği kullanılarak geçersiz kılınabilir.

## <a name="assembly-manifest-attributes"></a>Bütünleştirilmiş kod bildirim öznitelikleri

Derleme bildiriminde başlık, açıklama, varsayılan diğer ad ve yapılandırma dahil olmak üzere bilgi sağlamak için bütünleştirilmiş kod bildirim özniteliklerini kullanabilirsiniz. Aşağıdaki tabloda, derleme bildirim öznitelikleri açıklanmaktadır.

|Bütünleştirilmiş kod bildirim özniteliği|Açıklama|
|---------------------------------|-----------------|
|<xref:System.Reflection.AssemblyConfigurationAttribute>|Derlemenin, perakende veya hata ayıklama gibi yapılandırmasını gösteren dize değeri. Çalışma zamanı bu değeri kullanmaz.|
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|Başvurulan derlemelere göre kullanılacak varsayılan bir diğer ad belirten dize değeri. Bu değer, derlemenin kendisinin adı kolay değil (bir GUID değeri gibi) kolay bir ad sağlar. Bu değer, tam derleme adının kısa bir biçimi olarak da kullanılabilir.|
|<xref:System.Reflection.AssemblyDescriptionAttribute>|Derlemenin yapısını ve amacını özetleyen kısa bir açıklama belirten dize değeri.|
|<xref:System.Reflection.AssemblyTitleAttribute>|Derleme için kolay bir ad belirten dize değeri. Örneğin, *Comdlg* adlı bir derlemede Microsoft ortak Iletişim kutusu denetimi başlığı bulunabilir.|

## <a name="strong-name-attributes"></a>Tanımlayıcı ad öznitelikleri

Bir derleme için tanımlayıcı ad ayarlamak üzere tanımlayıcı ad öznitelikleri kullanabilirsiniz. Aşağıdaki tabloda tanımlayıcı ad öznitelikleri açıklanmaktadır.

|Tanımlayıcı ad özniteliği|Açıklama|
|----------------------------|-----------------|
|<xref:System.Reflection.AssemblyDelaySignAttribute>|Gecikme imzasının kullanıldığını gösteren Boolean değeri.|
|<xref:System.Reflection.AssemblyKeyFileAttribute>|Ortak anahtar (gecikme imzalamayı kullanıyorsanız) veya bu özniteliğin oluşturucusuna parametre olarak geçirilen ortak ve özel anahtarları içeren dosyanın adını gösteren dize değeri. Dosya adının, kaynak dosya yolu değil çıkış dosyası yoluna ( *. exe* veya *. dll*) göreli olduğunu unutmayın.|
|<xref:System.Reflection.AssemblyKeyNameAttribute>|Bu özniteliğin oluşturucusuna parametre olarak geçirilen anahtar çiftini içeren anahtar kapsayıcısını gösterir.|

Aşağıdaki kod örneğinde, *MyKey. snk*adlı ortak anahtar dosyası ile tanımlayıcı adlı bir derleme oluşturmak için Gecikmeli imzalama kullanılırken uygulanacak Öznitelikler gösterilmektedir.

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

- [Derlemeler oluştur](create.md)
- [Bütünleştirilmiş kod içeren program](program.md)
