---
title: -kaynak (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /resource
helpviewer_keywords:
- -resource compiler option [C#]
- /resource compiler option [C#]
- -res compiler option [C#]
- /res compiler option [C#]
- res compiler option [C#]
- resource compiler option [C#]
ms.assetid: 5212666e-98ab-47e4-a497-b5545ab15c7f
ms.openlocfilehash: e14bf59f5922a918b627af22c052c8efd9081e84
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69602531"
---
# <a name="-resource-c-compiler-options"></a>-kaynak (C# Derleyici Seçenekleri)
Belirtilen kaynağı çıktı dosyasına gömer.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-resource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
 `filename`  
 Çıktı dosyasına katıştırmak istediğiniz .NET Framework kaynak dosyası.  
  
 `identifier` (isteğe bağlı)  
 Kaynak için mantıksal ad; kaynağı yüklemek için kullanılan ad. Varsayılan, dosya adının adıdır.  
  
 `accessibility-modifier` (isteğe bağlı)  
 Kaynağın erişilebilirliği: ortak veya özel. Varsayılan değer herkese açıktır.  
  
## <a name="remarks"></a>Açıklamalar  
 Kaynağı derlemeye bağlamak ve kaynak dosyasını çıktı dosyasına eklememek için [-linkresource'ı](./linkresource-compiler-option.md) kullanın.  
  
 Varsayılan olarak, c# derleyicisi kullanılarak oluşturulan kaynaklar derlemede geneldir. Kaynakları özel yapmak için `private` erişilebilirlik değiştirici olarak belirtin. İzin verilen `public` veya `private` izin verilen başka bir erişilebilirlik yoktur.  
  
 Örneğin `filename` [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) veya geliştirme ortamında oluşturulan bir .NET Framework kaynak dosyasıysa, <xref:System.Resources> ad alanındaki üyelerle erişilebilir. Daha fazla bilgi için bkz. <xref:System.Resources.ResourceManager?displayProperty=nameWithType>. Diğer tüm kaynaklar için, çalışma <xref:System.Reflection.Assembly> zamanında kaynağa erişmek için sınıftaki `GetManifestResource` yöntemleri kullanın.  
  
 **-res** **-kaynak**kısa şeklidir.  
  
 Çıktı dosyasındaki kaynakların sırası komut satırında belirtilen sırada belirlenir.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1. Projenize bir kaynak dosyası ekleyin.  
  
2. **Çözüm Gezgini'ne**katıştırmak istediğiniz dosyayı seçin.  
  
3. **Özellikler** penceresindedosya için **Eylem Oluştur'u** seçin.  
  
4. **Yapı Eylemini** **Katıştırılmış Kaynağa**ayarlayın.  
  
 Bu derleyici seçeneğini programlı olarak nasıl ayarlayıştırılabilen ler hakkında bilgi için bkz. <xref:VSLangProj80.FileProperties2.BuildAction%2A>  
  
## <a name="example"></a>Örnek  
 Kaynak `in.cs` dosyayı `rf.resource`derleme ve ekleme:  
  
```console  
csc -resource:rf.resource in.cs  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
