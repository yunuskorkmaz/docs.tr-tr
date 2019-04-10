---
title: -win32manifest (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- /win32manifest compiler option [Visual Basic]
- win32manifest compiler option [Visual Basic]
- -win32manifest compiler option [Visual Basic]
ms.assetid: 9e3191b4-90db-41c8-966a-28036fd20005
ms.openlocfilehash: 15fe62457ed11ffcd08a1db3aa8be57080f22869
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59300804"
---
# <a name="-win32manifest-visual-basic"></a>-win32manifest (Visual Basic)
Bir projenin taşınabilir yürütülebilir (PE) dosya gömülü olması için kullanıcı tanımlı Win32 uygulama bildirim dosyası tanımlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-win32manifest: fileName  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terim|Tanım|  
|---|---|  
|`fileName`|Özel bildirim dosyasının yolu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Varsayılan olarak, Visual Basic Derleyicisi asInvoker istenen yürütme düzeyini belirten bir uygulama bildirimi katıştırır. Bildirim, yürütülebilir dosyayı oluşturulduğuna göre genellikle bin\Debug veya bin\Release klasörü, Visual Studio kullandığınızda aynı klasörde oluşturulur. Örneğin highestAvailable veya requireAdministrator istenen yürütme düzeyini belirtmek özel bir bildirim sağlamak istiyorsanız, dosya adını belirtmek için bu seçeneği kullanın.  
  
> [!NOTE]
>  Bu seçenek ve [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) seçeneği karşılıklı olarak birbirini dışlar. Aynı komut satırında iki seçenek de kullanmayı denerseniz, bir derleme hatası alırsınız.  
  
 Hiçbir uygulama bildirimini olan bir uygulama, Windows Vista kullanıcı hesabı denetimi özelliği altında dosya/kayıt defteri sanallaştırma istenen yürütme düzeyini tabi belirtir. Sanallaştırma hakkında daha fazla bilgi için bkz. [Windows Vista'da ClickOnce dağıtımı](/visualstudio/deployment/clickonce-deployment-on-windows-vista).  
  
 Aşağıdaki koşullardan biri doğru ise, uygulama sanallaştırma tabi olacaktır:  
  
1. Kullandığınız `-nowin32manifest` seçeneğini sağlamaz daha yeni bir derleme adımı veya bir Windows kaynağı (.res) dosyasının bir parçası olarak bir bildirim kullanarak `-win32resource` seçeneği.  
  
2. İstenen yürütme düzeyini belirtmeyen bir özel bildirim sağlar.  
  
 Visual Studio varsayılan .manifest dosyasını oluşturur ve hata ayıklama ve yayın dizinleri yürütülebilir dosyanın yanında depolar. Görüntüleyebilir veya tıklayarak varsayılan app.manifest dosyasını düzenleyin **UAC ayarları görüntüle** üzerinde **uygulama** Proje Tasarımcısı'nda sekmesi. Daha fazla bilgi için [uygulama sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).  
  
 Kullanarak bir Win32 kaynak dosyası bir parçası olarak veya özel bir derleme sonrası adımı olarak uygulama bildirimine sağlayabilirsiniz `-nowin32manifest` seçeneği. Uygulamanızın Windows Vista dosya veya kayıt defteri sanallaştırma tabi olmasını istiyorsanız, aynı bu seçeneği kullanın. Bu, oluşturma ve bir varsayılan bildirim PE dosyasına katıştırma derleyicinin engeller.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, Visual Basic Derleyicisi bir PE ekler, varsayılan bildirimi gösterir.  
  
> [!NOTE]
>  Derleyici bir standart uygulama adı MyApplication.app XML ekler. Windows Server 2003 Service Pack 3'üzerinde çalıştırılacak uygulamaları etkinleştirmek için geçici bir çözüm budur.  
  
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

- [Visual Basic Komut Satırı Derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [-nowin32manifest (Visual Basic)](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)
