---
title: /errorreport
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -errorreport compiler option [Visual Basic]
- /errorreport compiler option [Visual Basic]
- errorreport compiler option [Visual Basic]
ms.assetid: a7fe83a2-a6d8-460c-8dad-79a8f433f501
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0abe276aaacdeb175c3af7067dffa81448450e22
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="errorreport"></a>/errorreport
Belirtir nasıl [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] derleyici iç derleyici hataları rapor.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
/errorreport:{ prompt | queue | send | none }  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Bu seçenek rapor için kullanışlı bir yol sağlayan bir [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] iç derleyici hatası (çok) [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Microsoft ekibi. Varsayılan olarak, derleyici hiçbir bilgi Microsoft'a gönderir. Ancak, derleyici iç hatayla karşılaşırsanız, bu seçenek, Microsoft'a hata raporu olanak tanır. Bu bilgileri Microsoft mühendisleri nedenini yardımcı olur ve sonraki sürümü artırmanıza yardımcı olabilecek [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].  
  
 Bir kullanıcının, raporları göndermek becerisini makine ve kullanıcı ilkesi izinlerine bağlıdır.  
  
 Aşağıdaki tabloda özetlenmiştir etkisini `/errorreport` seçeneği.  
  
|Seçenek|Davranış|  
|---|---|  
|`prompt`|Bir iç derleyici hatası oluşursa, derleyici toplanan verilerin tam görüntüleyebilmesi için bir iletişim kutusu belirir. Hata raporunda herhangi bir önemli bilgi olup olmadığını belirlemek ve bir karar Microsoft'a gönderilip gönderilmeyeceğini yapın. Göndermeden karar ve makine ve kullanıcı ilke ayarlarını izin, derleyici verilerini Microsoft'a gönderir.|  
|`queue`|Hata raporu sıralar. Yönetici ayrıcalıklarıyla oturum kapatışınızda oturum en son ne zaman bu yana hataları bildirebilirsiniz (üç günde birden çok kez hata raporu göndermek için istenir değildir). Bu varsayılan davranıştır zaman `/errorreport` seçeneği belirtilmedi.|  
|`send`|Bir iç derleyici hatası olursa ve makine ve kullanıcı ilke ayarlarını izin derleyici verilerini Microsoft'a gönderir.<br /><br /> Seçenek `/errorReport:send` hata bilgilerini Microsoft'a otomatik olarak göndermeyi dener. Bu seçenek, kayıt defterine bağlıdır. Kayıt defterinde uygun değerleri ayarlama hakkında daha fazla bilgi için bkz: [Visual Studio 2008 komut satırı araçları'nda otomatik hata raporlamayı etkinleştirme](http://go.microsoft.com/fwlink/?LinkID=184695).|  
|`none`|Bir iç derleyici hatası oluşursa, onu değil toplanmayacak veya Microsoft'a gönderilir.|  
  
 Derleyici genellikle bazı kaynak kodu içeren hata, aynı anda yığını içeren verileri gönderir. Varsa `/errorreport` ile kullanılan [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) tüm kaynak dosyasına gönderilen seçeneği.  
  
 Bu seçenek en iyi ile kullanılan [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) Microsoft mühendisleri daha kolayca hatayı yeniden oluşturmaya izin verdiğinden seçeneği.  
  
> [!NOTE]
>  `/errorreport` Seçeneği Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derlerken kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod derleme girişiminde `T2.vb`, ve derleyici derleyici iç hatayla karşılaşırsa, hata raporunu Microsoft'a göndermek ister.  
  
```  
vbc /errorreport:prompt t2.vb  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Örnek derleme komut satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [/ bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)
