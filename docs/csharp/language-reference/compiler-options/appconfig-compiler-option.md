---
title: -appconfig (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /appconfig
helpviewer_keywords:
- /appconfig compiler option [C#]
- -appconfig compiler option [C#]
- appconfig compiler option [C#]
ms.assetid: 1cdbcbcc-7813-4010-b5b8-e67c107c5a98
ms.openlocfilehash: 7a7e8e61f65704a2e99385a1be320048d950324c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922517"
---
# <a name="-appconfig-c-compiler-options"></a>-appconfig (C# derleyici seçenekleri)
**-Appconfig** derleyici seçeneği, bir C# uygulamanın derlemenin uygulama yapılandırma (App. config) dosyasının konumunu derleme bağlama sırasında ortak DIL çalışma zamanı (CLR) olarak belirtmesini sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-appconfig:file  
```  
  
## <a name="arguments"></a>Arguments  
 `file`  
 Gerekli. Derleme bağlama ayarlarını içeren uygulama yapılandırma dosyası.  
  
## <a name="remarks"></a>Açıklamalar  
 Tek **appconfig** 'in kullanımı, bir derlemenin hem .NET Framework sürümüne hem de aynı anda belirli bir başvuru derlemesinin Silverlight sürümüne .NET Framework başvurması gereken gelişmiş senaryolardır. Örneğin, Windows Presentation Foundation (WPF) içinde yazılmış bir XAML tasarımcısının, tasarımcı 'nın Kullanıcı arabirimi için hem WPF masaüstüne hem de Silverlight 'ın içerdiği WPF 'nin alt kümesine başvurması gerekebilir. Aynı tasarımcı derlemesinin her iki derlemeye de erişimi vardır. Varsayılan olarak, derleme bağlaması iki derlemeyi eşdeğer olarak gördüğü için ayrı başvurular bir derleyici hatasına neden olur.  
  
 **-Appconfig** derleyici seçeneği, aşağıdaki örnekte gösterildiği gibi bir `<supportPortability>` etiketi kullanarak varsayılan davranışı devre dışı bırakan bir App. config dosyasının konumunu belirtmenize olanak sağlar.  
  
 `<supportPortability PKT="7cec85d7bea7798e" enable="false"/>`  
  
 Derleyici, dosyanın konumunu CLR 'nin derleme bağlama mantığına geçirir.  
  
> [!NOTE]
> Uygulamanızı derlemek için Microsoft Build Engine (MSBuild) kullanıyorsanız,. csproj dosyasına bir özellik etiketi ekleyerek **-appconfig** derleyici seçeneğini belirleyebilirsiniz. Projede zaten ayarlanmış olan App. config dosyasını kullanmak için,. csproj dosyasına özellik etiketi `<UseAppConfigForCompiler>` ekleyin ve değerini olarak `true`ayarlayın. Farklı bir App. config dosyası belirtmek için, özellik etiketi `<AppConfigForCompiler>` ekleyin ve değerini dosyanın konumuna ayarlayın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir uygulamanın hem .NET Framework uygulamasına hem de her iki uygulamada bulunan herhangi bir .NET Framework derlemesinin Silverlight uygulamasına .NET Framework başvurularına sahip olmasını sağlayan bir App. config dosyası gösterir. **-Appconfig** derleyici seçeneği bu app. config dosyasının konumunu belirtir.  
  
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

- [\<Supporttaşınabilirlik > öğesi](../../../framework/configure-apps/file-schema/runtime/supportportability-element.md)
- [Alfabetik Listelenmiş C# Derleyici Seçenekleri](./listed-alphabetically.md)
