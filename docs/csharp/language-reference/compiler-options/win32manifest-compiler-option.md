---
title: -win32manifest (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /win32manifest
helpviewer_keywords:
- /win32manifest compiler option [C#]
- win32manifest compiler option [C#]
- -win32manifest compiler option [C#]
ms.assetid: 9460ea1b-6c9f-44b8-8f73-301b30a01de1
ms.openlocfilehash: 24677b145974af03e6ddcac1b9bab5907ab70c7b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69924682"
---
# <a name="-win32manifest-c-compiler-options"></a>-win32manifest (C# Derleyici Seçenekleri)
Bir projenin taşınabilir yürütülebilir (PE) dosyasına katıştırılması için kullanıcı tanımlı Win32 uygulama bildirimi dosyasını belirtmek için **-win32manifest** seçeneğini kullanın.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-win32manifest: filename  
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
 `filename`  
 Özel bildirim dosyasının adı ve konumu.  
  
## <a name="remarks"></a>Açıklamalar  
 Varsayılan olarak, Visual C# derleyicisi istenen yürütme düzeyini belirten bir uygulama bildirimi "asInvoker" gömer. Görsel Studio'yu kullandığınızda, genellikle bin\Debug veya bin\Release klasörü olan yürütülebilir yapılının bulunduğu klasörde manifesto oluşturur. Örneğin, "en yüksek Kullanılabilir" veya "zorunlu Yönetici" için istenen yürütme düzeyini belirtmek için özel bir bildirim sağlamak istiyorsanız, dosyanın adını belirtmek için bu seçeneği kullanın.  
  
> [!NOTE]
> Bu seçenek ve [-win32res (C# Derleyici Seçenekleri)](./win32res-compiler-option.md) seçeneği birbirini dışlar. Her iki seçeneği de aynı komut satırında kullanmaya çalışırsanız bir yapı hatası alırsınız.  
  
 İstenen yürütme düzeyini belirten bir uygulama bildirimi olmayan bir uygulama, Windows'daki Kullanıcı Hesabı Denetimi özelliği altında dosya/kayıt defteri sanallaştırmasına tabi tutulur. Daha fazla bilgi için [Bkz. Kullanıcı Hesabı Denetimi.](/windows/access-protection/user-account-control/user-account-control-overview)  
  
 Bu koşullardan biri doğruysa, uygulamanız sanallaştırmaya tabi olacaktır:  
  
- **-nowin32manifest** seçeneğini kullanırsınız ve **-win32res** seçeneğini kullanarak daha sonraki bir yapı adımında veya Windows Resource (.res) dosyasının bir parçası olarak bir bildirim sağlamazsınız.  
  
- İstenen yürütme düzeyini belirtmeyen özel bir bildirim sağlarsınız.  
  
 Visual Studio varsayılan bir .manifest dosyası oluşturur ve yürütülebilir dosyanın yanında hata ayıklama ve sürüm dizinlerinde saklar. Herhangi bir metin düzenleyicisinde bir tane oluşturup sonra dosyayı projeye ekleyerek özel bir bildirim ekleyebilirsiniz. Alternatif olarak, **Çözüm Gezgini'nde** **Proje** simgesine sağ tıklayabilir, **Yeni Öğe Ekle'yi**tıklatın ve ardından Uygulama Bildirimi **Dosyası'nı**tıklatabilirsiniz. Yeni veya varolan bildirim dosyanızı ekledikten sonra, bu dosya **Bildirim** açılır listesinde görünür. Daha fazla bilgi için [Uygulama Sayfası, Proje Tasarımcısı (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp)sayfasına bakın.  
  
 [-nowin32manifest (C# Derleyici Seçenekleri)](./nowin32manifest-compiler-option.md) seçeneğini kullanarak uygulama bildirimini özel bir post-build adımı olarak veya Win32 kaynak dosyasının bir parçası olarak sağlayabilirsiniz. Uygulamanızın Windows Vista'da dosya veya kayıt defteri sanallaştırmasına tabi olmasını istiyorsanız aynı seçeneği kullanın. Bu, derleyicinin taşınabilir çalıştırılabilir (PE) dosyasına varsayılan bir bildirim oluşturmasını ve katıştırmasını önler.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, Visual C# derleyicisinin PE'ye ekleyen varsayılan bildirimi gösterir.  
  
> [!NOTE]
> Derleyici xml'e standart bir uygulama adı " MyApplication.app " ekler. Bu, uygulamaların Windows Server 2003 Hizmet Paketi 3'te çalışmasını sağlamak için geçici çözümdür.  
  
```xml  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
  <assemblyIdentity version="1.0.0.0" name="MyApplication.app"/>  
  <trustInfo xmlns="urn:schemas-microsoft-com:asm.v2">  
    <security>  
      <requestedPrivileges xmlns="urn:schemas-microsoft-com:asm.v3">  
        <requestedExecutionLevel level="asInvoker"/>  
      </requestedPrivileges>  
    </security>  
  </trustInfo>  
</assembly>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)
- [-nowin32manifest (C# Derleyici Seçenekleri)](./nowin32manifest-compiler-option.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
