---
title: End Deyimi
ms.date: 07/20/2015
f1_keywords:
- vb.End
- End
helpviewer_keywords:
- execution [Visual Basic], ending
- files [Visual Basic], closing
- End keyword [Visual Basic], End statements
- programs [Visual Basic], quitting
- code, exiting
- program termination
- End statement [Visual Basic]
- execution [Visual Basic], stopping
ms.assetid: 0e64467c-0f34-4aab-9ddd-43f8b9d55d90
ms.openlocfilehash: 864ac5ef1713f8ffa93c18accede8ecd5b3b7a8c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604438"
---
# <a name="end-statement"></a>End Deyimi
Yürütme hemen sonlandırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
End  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Yerleştireceğiniz `End` çalışmayı durdurmasına tüm uygulama zorlamak için bir yordam herhangi bir yere deyiminde. `End` ile açılan dosyaları kapatır bir `Open` deyimi ve uygulamanın tüm değişkenleri temizler. Uygulama nesnelerine başvurular bulunduran diğer program yok ve kendi kod hiçbiri çalışıyorsa hemen kapatılır.  
  
> [!NOTE]
>  `End` Deyimi kod yürütmeyi aniden durdurur ve çağrılamadı `Dispose` veya `Finalize` yöntemi veya başka bir Visual Basic kodu. Nesne başvuruları diğer programlar tarafından tutulan geçersiz kılınır. Varsa bir `End` deyimi karşılaştı içinde bir `Try` veya `Catch` denetim bloğu değil geçirmek karşılık gelen `Finally` bloğu.  
  
 `Stop` Deyimi askıya alır, ancak yürütme `End`, bırakmaz tüm dosyaları kapatın veya bir derlenmiş yürütülebilir dosyanın (.exe) dosyasında karşılaşılan sürece herhangi bir değişkeni temizleyin.  
  
 Çünkü `End` uygulamanızı katılımın olmadan sonlandırır açık olabilecek tüm kaynaklarına yakın düzgün bir şekilde kullanmadan önce aşağı denemelisiniz. Açık herhangi bir form uygulamanız varsa, örneğin, bunları denetim ulaştığında önce kapatmalısınız `End` deyimi.  
  
 Kullanmanız gereken `End` gerektiğinde ve yalnızca zaman hemen durdurmanız gerekir. Bir yordam sonlandırmak için normal şekilde ([dönüş deyimi](../../../visual-basic/language-reference/statements/return-statement.md) ve [çıkış deyimi](../../../visual-basic/language-reference/statements/exit-statement.md)) yalnızca yordamı düzgün bir şekilde kapatın, ancak ayrıca çağıran kodu Kapat düzgün bir şekilde aşağı fırsatı sunmak. Örneğin, bir konsol uygulaması kolayca kaldırabilirsiniz `Return` gelen `Main` yordamı.  
  
> [!IMPORTANT]
>  `End` Deyimi çağrıları <xref:System.Environment.Exit%2A> yöntemi <xref:System.Environment> sınıfını <xref:System> ad alanı. <xref:System.Environment.Exit%2A> sahip olmasını gerektiren `UnmanagedCode` izni. Aksi halde bir <xref:System.Security.SecurityException> hata oluşur.  
  
 Bir ek anahtar tarafından izlendiğinde [son \<anahtar sözcüğü > deyimi](../../../visual-basic/language-reference/statements/end-keyword-statement.md) uygun yordamı veya blok tanımını sonuna betimleyen. Örneğin, `End Function` tanımını sonlandırır bir `Function` yordamı.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır `End` kullanıcı isterse kod yürütmeyi sonlandırmak için deyimi.  
  
 [!code-vb[VbVersHelp60Controls#64](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/end-statement_1.vb)]  
  
## <a name="smart-device-developer-notes"></a>Akıllı Cihaz Geliştirici Notları  
 Bu deyim desteklenmiyor.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Security.Permissions.SecurityPermissionFlag>  
 [Stop Deyimi](../../../visual-basic/language-reference/statements/stop-statement.md)  
 [Son \<anahtar sözcüğü > deyimi](../../../visual-basic/language-reference/statements/end-keyword-statement.md)
