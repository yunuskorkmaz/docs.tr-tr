---
title: -appconfig (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /appconfig
helpviewer_keywords:
- /appconfig compiler option [C#]
- -appconfig compiler option [C#]
- appconfig compiler option [C#]
ms.assetid: 1cdbcbcc-7813-4010-b5b8-e67c107c5a98
ms.openlocfilehash: 7a7e8e61f65704a2e99385a1be320048d950324c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69922517"
---
# <a name="-appconfig-c-compiler-options"></a>-appconfig (C# Derleyici Seçenekleri)
**-appconfig** derleyici seçeneği, bir C# uygulamasının derleme bağlama zamanında ortak dil çalışma süresine (CLR) bir derlemenin uygulama yapılandırması (app.config) dosyasının konumunu belirtmesini sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-appconfig:file  
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
 `file`  
 Gereklidir. Derleme bağlama ayarlarını içeren uygulama yapılandırma dosyası.  
  
## <a name="remarks"></a>Açıklamalar  
 **-appconfig'in** bir kullanımı, bir derlemenin hem .NET Framework sürümüne hem de belirli bir başvuru derlemesinin Silverlight için .NET Framework sürümüne aynı anda başvurmak zorunda olduğu gelişmiş senaryolardır. Örneğin, Windows Sunu Vakfı'nda (WPF) yazılmış bir XAML tasarımcısının, tasarımcının kullanıcı arabirimi için hem WPF Masaüstü'ne hem de Silverlight ile birlikte verilen WPF alt kümesine başvurması gerekebilir. Aynı tasarımcı derlemesi her iki derlemeye de erişmek zorundadır. Derleme bağlama iki derlemeyi eşdeğer olarak gördüğünden, varsayılan olarak, ayrı başvurular derleyici hatasına neden olur.  
  
 **-appconfig** derleyici seçeneği, aşağıdaki örnekte gösterildiği gibi, bir `<supportPortability>` etiket kullanarak varsayılan davranışı devre dışı düşüren bir app.config dosyasının konumunu belirtmenizi sağlar.  
  
 `<supportPortability PKT="7cec85d7bea7798e" enable="false"/>`  
  
 Derleyici, dosyanın konumunu CLR'nin derleme bağlama mantığına geçirir.  
  
> [!NOTE]
> Uygulamanızı oluşturmak için Microsoft Build Engine 'i (MSBuild) kullanıyorsanız, .csproj dosyasına bir özellik etiketi ekleyerek **-appconfig** derleyicisi seçeneğini ayarlayabilirsiniz. Projede zaten ayarlanmış olan app.config dosyasını kullanmak `<UseAppConfigForCompiler>` için ,.csproj dosyasına özellik `true`etiketi ekleyin ve değerini . Farklı bir app.config dosyası belirtmek `<AppConfigForCompiler>` için özellik etiketi ekleyin ve değerini dosyanın konumuna ayarlayın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir uygulamanın hem .NET Framework uygulamasına hem de .NET Framework derlemesinde var olan herhangi bir .NET Framework derlemesinin Silverlight uygulamasına atıfta bulunmasını sağlayan bir app.config dosyasını gösterir. **-appconfig** derleyici seçeneği bu app.config dosyasının konumunu belirtir.  
  
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

- [\<destekTaşınabilirlik> Elemanı](../../../framework/configure-apps/file-schema/runtime/supportportability-element.md)
- [Alfabetik Listelenmiş C# Derleyici Seçenekleri](./listed-alphabetically.md)
