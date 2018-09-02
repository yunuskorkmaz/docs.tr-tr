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
ms.openlocfilehash: 88932ad30e30d53312e6d76f70415969b9e86675
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43468234"
---
# <a name="-win32manifest-c-compiler-options"></a>-win32manifest (C# Derleyici Seçenekleri)
Kullanım **-win32manifest** projenin taşınabilir yürütülebilir (PE) dosya gömülü olması için bir kullanıcı tanımlı uygulama soubor manifestu Win32 için seçeneği.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-win32manifest: filename  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Özel bildirim dosyasının konumunu ve adını.  
  
## <a name="remarks"></a>Açıklamalar  
 Varsayılan olarak, Visual C# derleyicisi "asInvoker" istenen yürütme düzeyini belirten bir uygulama bildirimi katıştırır. Bildirim, yürütülebilir dosya oluşturulduğuna göre genellikle bin\Debug veya bin\Release klasörü, Visual Studio kullandığınızda aynı klasörde oluşturulur. Örneğin "highestAvailable" veya "requireAdministrator" istenen yürütme düzeyini belirtmek özel bir bildirim sağlamak istiyorsanız, dosya adını belirtmek için bu seçeneği kullanın.  
  
> [!NOTE]
>  Bu seçenek ve [-win32res (C# Derleyici Seçenekleri)](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) seçeneği karşılıklı olarak birbirini dışlar. Aynı komut satırında iki seçenek de kullanmayı denerseniz bir derleme hatası alırsınız.  
  
 Hiçbir uygulama bildirimini olan bir uygulama, istenen yürütme düzeyini dosya/kayıt defteri sanallaştırma Windows kullanıcı hesabı denetimi özelliği altında tabi belirtir. Daha fazla bilgi için [kullanıcı hesabı denetimi](/windows/access-protection/user-account-control/user-account-control-overview).  
  
 Bu koşullardan biri doğru ise, uygulama sanallaştırma tabi olacaktır:  
  
-   Kullandığınız **-nowin32manifest** seçeneğini sağlamaz daha yeni bir derleme adımı veya bir Windows kaynağı (.res) dosyasının bir parçası olarak bir bildirim kullanarak **-win32res** seçeneği.  
  
-   İstenen yürütme düzeyini belirtmeyen bir özel bildirim sağlar.  
  
 Visual Studio varsayılan .manifest dosyasını oluşturur ve hata ayıklama ve yayın dizinleri yürütülebilir dosyanın yanında depolar. Herhangi bir metin düzenleyicisinde oluşturma ve sonra dosyayı projeye ekleyerek, özel bir bildirim ekleyebilirsiniz. Alternatif olarak, sağ **proje** simgesini **Çözüm Gezgini**, tıklayın **Yeni Öğe Ekle**ve ardından **uygulama bildirim dosyası**. Yeni veya var olan bildirim dosyası ekledikten sonra görüneceği **bildirim** açılan liste. Daha fazla bilgi için [uygulama sayfası, Proje Tasarımcısı (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).  
  
 Kullanarak bir Win32 kaynak dosyası bir parçası olarak veya özel bir derleme sonrası adımı olarak uygulama bildirimine sağlayabilirsiniz [-nowin32manifest (C# Derleyici Seçenekleri)](../../../csharp/language-reference/compiler-options/nowin32manifest-compiler-option.md) seçeneği. Uygulamanızın Windows Vista dosya veya kayıt defteri sanallaştırma tabi olmasını istiyorsanız, aynı bu seçeneği kullanın. Bu, derleyicinin oluşturmasını ve taşınabilir yürütülebilir (PE) dosyasında bir varsayılan bildirim gömülüyor engeller.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, Visual C# derleyicisinin bir PE ekler, varsayılan bildirimi gösterir.  
  
> [!NOTE]
>  Derleyicinin, xml verilerinin standart uygulama adı "MyApplication.app şeklinde" ekler. Windows Server 2003 Service Pack 3'üzerinde çalıştırılacak uygulamaları etkinleştirmek için geçici bir çözüm budur.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  

- [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)  
- [-nowin32manifest (C# Derleyici Seçenekleri)](../../../csharp/language-reference/compiler-options/nowin32manifest-compiler-option.md)  
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
