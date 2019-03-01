---
title: End deyimi (Visual Basic)
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
ms.openlocfilehash: 8b189449044a48432a6cf05b75f39581be111495
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56979543"
---
# <a name="end-statement"></a>End Deyimi
Yürütmeyi hemen sonlanır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
End  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Koyabilirsiniz `End` yordamındaki durmaya uygulamanın tamamı zorlamak için her yerden bir. `End` açılmış neden olan tüm dosyaları kapatır bir `Open` deyimi ve uygulamanın tüm değişkenleri temizler. Uygulama nesnelerini için başvuru bulunduran başka bir program vardır ve kendi kod hiçbiri çalıştıran hemen kapatır.  
  
> [!NOTE]
>  `End` Deyimi yürütmeyi aniden durdurur ve çağrılamadı `Dispose` veya `Finalize` yöntemi veya başka bir Visual Basic kod. Diğer programları tarafından tutulan nesne başvuruları geçersiz kılınır. Varsa bir `End` deyimi içinde karşılaşıldığında bir `Try` veya `Catch` denetim bloğu değil geçirmek karşılık gelen `Finally` blok.  
  
 `Stop` Deyimi askıya alır, ancak yürütme `End`, tüm dosyaları kapatın veya desteklemez derlenmiş yürütülebilir (.exe) dosyasında karşılaşılanaa sürece herhangi bir değişkeni temizleyin.  
  
 Çünkü `End` uygulamanıza katılan sonlandırır açık olabilecek herhangi bir kaynakta, yakın düzgün bir şekilde kullanmadan önce aşağı denemelisiniz. Uygulamanızı açın herhangi bir form varsa, örneğin, bunları önce denetim ulaştığında kapatmalısınız `End` deyimi.  
  
 Kullanmanız gereken `End` tutumlu ve yalnızca gerektiğinde hemen durdurmak. Bir yordam sonlandırmak için normal şekilde ([dönüş deyimi](../../../visual-basic/language-reference/statements/return-statement.md) ve [çıkış bildirimi](../../../visual-basic/language-reference/statements/exit-statement.md)) yalnızca yordamı düzgün bir şekilde kapatın, ancak aynı zamanda çağıran kodun temiz kapatma aşağı fırsatı sunmak. Örneğin, bir konsol uygulaması kolayca kaldırabilirsiniz `Return` gelen `Main` yordamı.  
  
> [!IMPORTANT]
>  `End` Deyim aramaları <xref:System.Environment.Exit%2A> yöntemi <xref:System.Environment> sınıfını <xref:System> ad alanı. <xref:System.Environment.Exit%2A> sahip olmasını gerektirir `UnmanagedCode` izni. Değilse, bunu yaparsanız bir <xref:System.Security.SecurityException> hata oluşur.  
  
 Ek bir anahtar tarafından izlendiğinde [son \<anahtar sözcüğü > deyimi](../../../visual-basic/language-reference/statements/end-keyword-statement.md) uygun yordamı ya da blok tanımının sonuna betimleyen. Örneğin, `End Function` tanımını sonlandırır bir `Function` yordamı.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `End` kullanıcı isterse kod yürütmeyi sona erdirmek için deyimi.  
  
 [!code-vb[VbVersHelp60Controls#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVersHelp60Controls/VB/Form1.vb#64)]  
  
## <a name="smart-device-developer-notes"></a>Akıllı Cihaz Geliştirici Notları  
 Bu deyimi desteklenmiyor.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Security.Permissions.SecurityPermissionFlag>
- [Stop Deyimi](../../../visual-basic/language-reference/statements/stop-statement.md)
- [Son \<anahtar sözcüğü > deyimi](../../../visual-basic/language-reference/statements/end-keyword-statement.md)
