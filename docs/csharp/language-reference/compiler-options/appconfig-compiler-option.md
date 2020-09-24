---
description: -appconfig (C# derleyici seçenekleri)
title: -appconfig (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /appconfig
helpviewer_keywords:
- /appconfig compiler option [C#]
- -appconfig compiler option [C#]
- appconfig compiler option [C#]
ms.assetid: 1cdbcbcc-7813-4010-b5b8-e67c107c5a98
ms.openlocfilehash: 8ee481851dc02bed5eb0a7c26fa8893e52d54a9f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157973"
---
# <a name="-appconfig-c-compiler-options"></a>-appconfig (C# derleyici seçenekleri)

**-Appconfig** derleyici seçeneği, bir C# uygulamasının derleme bağlama süresinde ortak dil çalışma zamanına (CLR) bir derlemenin uygulama yapılandırma (app.config) dosyasının konumunu belirtmesini sağlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
```console  
-appconfig:file  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `file`  
 Gereklidir. Derleme bağlama ayarlarını içeren uygulama yapılandırma dosyası.  
  
## <a name="remarks"></a>Açıklamalar  

 Tek **appconfig** 'in kullanımı, bir derlemenin hem .NET Framework sürümüne hem de aynı anda belirli bir başvuru derlemesinin Silverlight sürümüne .NET Framework başvurması gereken gelişmiş senaryolardır. Örneğin, Windows Presentation Foundation (WPF) içinde yazılmış bir XAML tasarımcısının, tasarımcı 'nın Kullanıcı arabirimi için hem WPF masaüstüne hem de Silverlight 'ın içerdiği WPF 'nin alt kümesine başvurması gerekebilir. Aynı tasarımcı derlemesinin her iki derlemeye de erişimi vardır. Varsayılan olarak, derleme bağlaması iki derlemeyi eşdeğer olarak gördüğü için ayrı başvurular bir derleyici hatasına neden olur.  
  
 **-Appconfig** derleyici seçeneği, `<supportPortability>` Aşağıdaki örnekte gösterildiği gibi bir etiketi kullanarak varsayılan davranışı devre dışı bırakan bir app.config dosyasının konumunu belirtmenize olanak sağlar.  
  
 `<supportPortability PKT="7cec85d7bea7798e" enable="false"/>`  
  
 Derleyici, dosyanın konumunu CLR 'nin derleme bağlama mantığına geçirir.  
  
> [!NOTE]
> Uygulamanızı derlemek için Microsoft Build Engine (MSBuild) kullanıyorsanız,. csproj dosyasına bir özellik etiketi ekleyerek **-appconfig** derleyici seçeneğini belirleyebilirsiniz. Projede zaten ayarlanmış olan app.config dosyasını kullanmak için, `<UseAppConfigForCompiler>` . csproj dosyasına özellik etiketi ekleyin ve değerini olarak ayarlayın `true` . Farklı bir app.config dosyası belirtmek için, özellik etiketi ekleyin `<AppConfigForCompiler>` ve değerini dosyanın konumuna ayarlayın.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, bir uygulamanın hem .NET Framework .NET Framework uygulamasına hem de her iki uygulamada bulunan herhangi bir .NET Framework derlemesinin Silverlight uygulamasına yönelik başvurularına sahip olmasını sağlayan bir app.config dosyası gösterir. **-Appconfig** derleyici seçeneği bu app.config dosyasının konumunu belirtir.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [\<supportPortability> Dosyalarında](../../../framework/configure-apps/file-schema/runtime/supportportability-element.md)
- [Alfabetik Listelenmiş C# Derleyici Seçenekleri](./listed-alphabetically.md)
