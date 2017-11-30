---
title: /linkresource (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /linkresource compiler option [Visual Basic]
- -linkresource compiler option [Visual Basic]
- linkresource compiler option [Visual Basic]
- /linkres compiler option [Visual Basic]
- linkres compiler option [Visual Basic]
- -linkres compiler option [Visual Basic]
ms.assetid: cf4dcad8-17b7-404c-9184-29358aa05b15
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4e51f844695985485210a1e4bedfef7ac968326c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="linkresource-visual-basic"></a>/linkresource (Visual Basic)
Yönetilen kaynak bağlantısını oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
/linkresource:filename[,identifier[,public|private]]  
' -or-  
/linkres:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Gerekli. Derlemeye bağlamak için kaynak dosyası. Dosya adı boşluk içeriyorsa adı tırnak işaretleri içine alın ("").  
  
 `identifier`  
 İsteğe bağlı. Kaynak için mantıksal adı. Kaynak yüklemek için kullanılan ad. Varsayılan dosya adıdır. İsteğe bağlı olarak, dosya gibi ortak veya özel derleme bildiriminde olup olmadığını belirtebilirsiniz: `/linkres:filename.res,myname.res,public`. Varsayılan olarak, `filename` bütünleştirilmiş kodunda geneldir.  
  
## <a name="remarks"></a>Açıklamalar  
 `/linkresource` Seçeneği değil katıştırmak kaynak dosyasını çıktı dosyasına; kullanın `/resource` Bunu yapmak için seçeneği.  
  
 `/linkresource` Seçeneği birini gerektirir `/target` dışında seçenekleri `/target:module`.  
  
 Varsa `filename` olan bir [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] , örneğin, tarafından oluşturulan kaynak dosyasını [Resgen.exe (kaynak dosya oluşturucu)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) veya geliştirme ortamında üyelerle erişilebileceğini <xref:System.Resources> ad alanı. (Daha fazla bilgi için bkz: <xref:System.Resources.ResourceManager>.) Çalışma zamanında tüm diğer kaynaklarına erişmek için ile başlayan yöntemleri kullanan `GetManifestResource` içinde <xref:System.Reflection.Assembly> sınıfı.  
  
 Dosya adı herhangi bir dosya biçiminde olabilir. Örneğin, böylece genel derleme önbelleğine yüklü ve yönetilen kod derlemesindeki erişilen derleme yerel bir DLL parçası haline getirmek isteyebilirsiniz.  
  
 Kısa formunu `/linkresource` olan `/linkres`.  
  
> [!NOTE]
>  `/linkresource` Seçeneği Visual Studio geliştirme ortamından kullanılabilir değil; komut satırından derleme zaman yalnızca kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod derlerken `In.vb` ve kaynak dosyası bağlantılar `Rf.resource`.  
  
```  
vbc /linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/ target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [/ Resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md)  
 [Örnek derleme komut satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
