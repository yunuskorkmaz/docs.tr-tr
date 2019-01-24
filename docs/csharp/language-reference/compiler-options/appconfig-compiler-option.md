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
ms.openlocfilehash: 102ed3977d56ace0dab63b1f066cc10a6fc5dfbf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54514068"
---
# <a name="-appconfig-c-compiler-options"></a>-appconfig (C# Derleyici Seçenekleri)
**- Appconfig** derleyici seçeneği, derleme bağlama zamanında ortak dil çalışma zamanı (CLR) için bir derlemenin uygulama yapılandırma (app.config) dosyasının konumunu belirtmek bir C# uygulaması sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-appconfig:file  
```  
  
## <a name="arguments"></a>Arguments  
 `file`  
 Gerekli. Derleme bağlama ayarlarını içeren uygulama yapılandırma dosyası.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir kullanımını **- appconfig** senaryolarında bir derleme bulunduğu hem .NET Framework sürümü hem de Silverlight sürümü aynı anda belirli bir başvuru bütünleştirilmiş kodu için .NET Framework başvurmak Gelişmiş. Örneğin, Windows Presentation Foundation (WPF) yazılı bir XAML tasarımcının hem WPF Masaüstü Tasarımcısı kullanıcı arabirimi ve Silverlight ile gelen WPF alt kümesi için başvuru gerekebilir. Tasarımcı aynı derlemenin iki derleme erişmelidir. Varsayılan olarak, derleme bağlama iki derlemeyi eşdeğer olarak gördüğünden ayrı başvurular bir derleyici hatasına neden olur.  
  
 **- Appconfig** derleyici seçeneği kullanılarak varsayılan davranışı devre dışı bırakan bir app.config dosyasının konumunu belirtmenize imkan tanır bir `<supportPortability>` , aşağıdaki örnekte gösterildiği gibi etiketleyin.  
  
 `<supportPortability PKT="7cec85d7bea7798e" enable="false"/>`  
  
 Derleyici dosyasının konumu CLR'ın derleme bağlama mantığına geçirir.  
  
> [!NOTE]
>  Uygulamanızı oluşturmak üzere Microsoft Build Engine (MSBuild) kullanıyorsanız, ayarlayabileceğiniz **- appconfig** için .csproj dosyasını bir özellik etiketi ekleyerek derleyici seçeneği. Projede zaten ayarlanmış ve app.config dosyasında kullanılacak özellik etiketi ekleyin `<UseAppConfigForCompiler>` için .csproj dosyasını ve değerini ayarlamak `true`. Farklı bir app.config dosyası belirtmek için özellik etiketi ekleyin `<AppConfigForCompiler>` ve dosya konumuna değerini ayarlayın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir uygulama hem .NET Framework uygulamasına hem de her iki uygulamada da bulunan herhangi bir .NET Framework derlemesinin Silverlight için .NET Framework başvuru sağlayan bir app.config dosyasını gösterir. **- Appconfig** derleyici seçeneği bu app.config dosyasının konumunu belirtir.  
  
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

- [\<supportPortability > öğesi](../../../framework/configure-apps/file-schema/runtime/supportportability-element.md)
- [Alfabetik Listelenmiş C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)
