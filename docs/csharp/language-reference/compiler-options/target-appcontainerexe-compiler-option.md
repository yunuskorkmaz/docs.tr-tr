---
title: "-target: appcontainerexe (C# Derleyici Seçenekleri)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
ms.assetid: e7e62229-23ea-4e53-bef5-380d951bf95f
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 61fc914b0d956bcca8e0d574296fa0723b0e1406
ms.sourcegitcommit: 973a12d1e6962cd9a9c263fbfaad040ec8267fe9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/22/2018
---
# <a name="-targetappcontainerexe-c-compiler-options"></a>-target: appcontainerexe (C# Derleyici Seçenekleri)
Kullanırsanız **-target: appcontainerexe** derleyici seçeneği derleyici bir uygulama kapsayıcısında çalıştırılması gereken bir Windows yürütülebilir dosyanın (.exe) dosyası oluşturur. Bu seçenek eşdeğerdir [-target: winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md) için tasarlanmıştır ancak [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] uygulamalar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-target:appcontainerexe  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Bir uygulama kapsayıcısında çalıştırmak için uygulamayı gerektirmek için bu seçeneği bir bit ayarlar [taşınabilir yürütülebilir](https://msdn.microsoft.com/library/windows/desktop/ms680547(v=vs.85).aspx?id=19509) (PE) dosyası. Bu bit ayarlandığında, bir uygulama kapsayıcısı dışında yürütülebilir dosyayı başlatma CreateProcess yöntemi çalışırsa, bir hata oluşur.  
  
 Kullanmadığınız sürece [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) seçeneği, çıktı dosyası adını içeren giriş dosyası adını alır [ana](../../../csharp/programming-guide/main-and-command-args/index.md) yöntemi.  
  
 Tüm bir komut isteminde bu seçeneği belirttiğinizde, sonraki kadar dosyaları **-out** veya **-hedef** seçeneği yürütülebilir dosyayı oluşturmak için kullanılır.  
  
### <a name="to-set-this-compiler-option-in-the-ide"></a>Bu derleyici seçeneğini IDE içinde ayarlamak için  
  
1.  İçinde **Çözüm Gezgini**projeniz için kısayol menüsünü açın ve ardından **özellikleri**.  
  
2.  Üzerinde **uygulama** sekmesinde **çıktı türü** listesinde, seçin **Windows mağazası uygulaması**.  
  
     Bu seçenek yalnızca için kullanılabilir [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] uygulama şablonları.  
  
 Bu derleyici seçeneği programlı olarak nasıl ayarlanacağı hakkında daha fazla bilgi için bkz: <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki komut derlerken `filename.cs` yalnızca bir uygulama kapsayıcısında çalıştırılabilir bir Windows yürütülebilir dosyaya.  
  
```console  
csc -target:appcontainerexe filename.cs  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [-target (C# Derleyici Seçenekleri)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
 [-target:winexe (C# Compiler Options)](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md)  
 [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)
