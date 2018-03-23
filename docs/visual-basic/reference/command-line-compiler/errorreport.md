---
title: -errorreport
ms.date: 03/10/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -errorreport compiler option [Visual Basic]
- /errorreport compiler option [Visual Basic]
- errorreport compiler option [Visual Basic]
ms.assetid: a7fe83a2-a6d8-460c-8dad-79a8f433f501
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 59dc833299161eac7b119e654c94534f202b1cb7
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2018
---
# <a name="-errorreport"></a>-errorreport
Belirtir nasıl [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] derleyici iç derleyici hataları rapor.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-errorreport:{ prompt | queue | send | none }  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Bu seçenek rapor için kullanışlı bir yol sağlayan bir [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] iç derleyici hatası (çok) [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Microsoft ekibi. Varsayılan olarak, derleyici hiçbir bilgi Microsoft'a gönderir. Ancak, derleyici iç hatayla karşılaşırsanız, bu seçenek, Microsoft'a hata raporu olanak tanır. Bu bilgileri Microsoft mühendisleri nedenini yardımcı olur ve sonraki sürümü artırmanıza yardımcı olabilecek [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].  
  
 Bir kullanıcının, raporları göndermek becerisini makine ve kullanıcı ilkesi izinlerine bağlıdır.  
  
 Aşağıdaki tabloda özetlenmiştir etkisini `-errorreport` seçeneği.  
  
|Seçenek|Davranış|  
|---|---|  
|`prompt`|Bir iç derleyici hatası oluşursa, derleyici toplanan verilerin tam görüntüleyebilmesi için bir iletişim kutusu belirir. Hata raporunda herhangi bir önemli bilgi olup olmadığını belirlemek ve bir karar Microsoft'a gönderilip gönderilmeyeceğini yapın. Göndermeden karar ve makine ve kullanıcı ilke ayarlarını izin, derleyici verilerini Microsoft'a gönderir.|  
|`queue`|Hata raporu sıralar. Yönetici ayrıcalıklarıyla oturum kapatışınızda oturum en son ne zaman bu yana hataları bildirebilirsiniz (üç günde birden çok kez hata raporu göndermek için istenir değildir). Bu varsayılan davranıştır zaman `-errorreport` seçeneği belirtilmedi.|  
|`send`|Bir iç derleyici hatası olursa ve makine ve kullanıcı ilke ayarlarını izin derleyici verilerini Microsoft'a gönderir.<br /><br /> Seçenek `-errorreport:send` hata bilgilerini Microsoft'a otomatik olarak göndermeyi dener. Bu seçenek, kayıt defterine bağlıdır. Kayıt defterinde uygun değerleri ayarlama hakkında daha fazla bilgi için bkz: [Visual Studio 2008 komut satırı araçları'nda otomatik hata raporlamayı etkinleştirme](http://go.microsoft.com/fwlink/?LinkID=184695).|  
|`none`|Bir iç derleyici hatası oluşursa, onu değil toplanmayacak veya Microsoft'a gönderilir.|  
  
 Derleyici genellikle bazı kaynak kodu içeren hata, aynı anda yığını içeren verileri gönderir. Varsa `-errorreport` ile kullanılan [- bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) tüm kaynak dosyasına gönderilen seçeneği.  
  
 Bu seçenek en iyi ile kullanılan [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) Microsoft mühendisleri daha kolayca hatayı yeniden oluşturmaya izin verdiğinden seçeneği.  
  
> [!NOTE]
>  `-errorreport` Seçeneği Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derlerken kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod derleme girişiminde `T2.vb`, ve derleyici derleyici iç hatayla karşılaşırsa, hata raporunu Microsoft'a göndermek ister.  
  
```  
vbc -errorreport:prompt t2.vb  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)
