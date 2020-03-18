---
title: -hedef:appcontainerexe (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
ms.assetid: e7e62229-23ea-4e53-bef5-380d951bf95f
ms.openlocfilehash: 64661e72f9efe190606cadd93558678cb849e8cc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74204532"
---
# <a name="-targetappcontainerexe-c-compiler-options"></a>-hedef:appcontainerexe (C# Derleyici Seçenekleri)
**-target:appcontainerexe** derleyici seçeneğini kullanırsanız, derleyici bir uygulama kapsayıcısında çalıştırılması gereken bir Windows çalıştırılabilir (.exe) dosyası oluşturur. Bu seçenek [-hedef:winexe'ye](./target-winexe-compiler-option.md) eşdeğerdir, ancak Windows 8.x Store uygulamaları için tasarlanmıştır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-target:appcontainerexe  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Uygulamanın bir uygulama kapsayıcısında çalışmasını gerektirmek için, bu seçenek [Taşınabilir Yürütülebilir](/windows/desktop/Debug/pe-format) (PE) dosyasında biraz ayarlar. Bu bit ayarlandığında, CreateProcess yöntemi yürütülebilir dosyayı bir uygulama kapsayıcısının dışına başlatmaya çalışırsa bir hata oluşur.  
  
 [-out](./out-compiler-option.md) seçeneğini kullanmadığınız sürece, çıktı dosyası adı [Ana](../../programming-guide/main-and-command-args/index.md) yöntemi içeren giriş dosyasının adını alır.  
  
 Bu seçeneği komut isteminde belirttiğiniz zaman, yürütülebilir dosyayı oluşturmak için bir sonraki **-out** **veya-hedef** seçeneğine kadar tüm dosyalar kullanılır.  
  
### <a name="to-set-this-compiler-option-in-the-ide"></a>Bu derleyici seçeneğini IDE içinde ayarlamak için  
  
1. **Çözüm Gezgini'nde,** projenizin kısayol menüsünü açın ve ardından **Özellikler'i**seçin.  
  
2. **Uygulama** sekmesinde, **Çıktı türü** listesinde **Windows Mağazası Uygulamasını**seçin.  
  
     Bu seçenek yalnızca Windows 8.x Store uygulama şablonları için kullanılabilir.  
  
 Bu derleyici seçeneğini programlı olarak nasıl ayarlayıştırılabilen ler hakkında bilgi için bkz. <xref:VSLangProj80.ProjectProperties3.OutputType%2A>  
  
## <a name="example"></a>Örnek  
 Aşağıdaki komut, `filename.cs` yalnızca bir uygulama kapsayıcısında çalıştırılabilen bir Windows çalıştırılabilir dosyasında derler.  
  
```console  
csc -target:appcontainerexe filename.cs  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [-hedef (C# Derleyici Seçenekleri)](./target-compiler-option.md)
- [-hedef:winexe (C# Derleyici Seçenekleri)](./target-winexe-compiler-option.md)
- [C# Derleyici Seçenekleri](./index.md)
