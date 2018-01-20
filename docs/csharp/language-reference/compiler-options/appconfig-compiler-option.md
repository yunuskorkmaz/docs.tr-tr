---
title: "-appconfig (C# Derleyici Seçenekleri)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /appconfig
helpviewer_keywords:
- /appconfig compiler option [C#]
- -appconfig compiler option [C#]
- appconfig compiler option [C#]
ms.assetid: 1cdbcbcc-7813-4010-b5b8-e67c107c5a98
caps.latest.revision: "26"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a3f2c1bc9d0d3fec0635d284f64138f0432f59ef
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="-appconfig-c-compiler-options"></a>-appconfig (C# Derleyici Seçenekleri)
**- Appconfig** derleyici seçeneği derleme bağlama zamanında ortak dil çalışma zamanı (CLR) için bir derlemenin uygulama yapılandırması (app.config) dosyasının konumunu belirtmek C# uygulaması sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-appconfig:file  
```  
  
## <a name="arguments"></a>Arguments  
 `file`  
 Gerekli. Derleme bağlama ayarları içeren uygulama yapılandırma dosyası.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir kullanımını **- appconfig** Gelişmiş senaryoları bütünleştirilmiş olduğu .NET Framework sürümünü ve aynı anda belirli referans derlemesini Silverlight sürümü için .NET Framework başvurmak. Örneğin, Windows Presentation Foundation (WPF) yazılmış bir XAML Tasarımcısı hem WPF Masaüstü için tasarımcının kullanıcı arabirimi ve Silverlight ile gelen WPF alt başvuru gerekebilir. Her iki derlemeleri erişmek aynı tasarımcı derlemesi vardır. Derleme bağlama eşdeğer olarak iki derleme gördüğünden varsayılan olarak, bir derleyici hatası ayrı başvuruları neden.  
  
 **- Appconfig** derleyici seçeneği sağlar, kullanarak varsayılan davranışı devre dışı bırakan bir app.config dosyasının konumunu belirtmek bir `<supportPortability>` , aşağıdaki örnekte gösterildiği gibi etiketi.  
  
 `<supportPortability PKT="7cec85d7bea7798e" enable="false"/>`  
  
 Derleyici dosyasının konumunu CLR'nin derleme bağlama mantığı geçirir.  
  
> [!NOTE]
>  Uygulamanızı yapılandırmak için Microsoft Build Engine (MSBuild) kullanıyorsanız, ayarlayabileceğiniz **- appconfig** .csproj dosyasına bir özellik etiketi ekleyerek derleyici seçeneği. Projede zaten ayarlanmış app.config dosyasını kullanmak için özellik etiketi ekleyin `<UseAppConfigForCompiler>` .csproj için dosya ve değerini ayarlama `true`. Farklı bir app.config dosyası belirtmek için özellik etiketi ekleyin `<AppConfigForCompiler>` ve dosya konumuna değerini ayarlayın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir uygulama hem .NET Framework uygulamasını hem de her iki uygulamada da bulunan herhangi bir .NET Framework derlemesinin Silverlight uygulama için .NET Framework başvuran sağlayan bir app.config dosyasını gösterir. **- Appconfig** derleyici seçeneği bu app.config dosyasının konumunu belirtir.  
  
```xml  
<configuration>  
      <runtime>  
      <assemblyBinding>  
            <supportPortability PKT="7cec85d7bea7798e" enable="false"/>  
            <supportPortability PKT="31bf3856ad364e35" enable="false"/>  
      </assemblyBinding>  
      </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [\<supportPortability > öğesi](../../../framework/configure-apps/file-schema/runtime/supportportability-element.md)  
 [Alfabetik Listelenmiş C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)
