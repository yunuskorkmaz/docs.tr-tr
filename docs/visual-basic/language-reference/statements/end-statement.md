---
title: End ekstresi (Visual Basic)
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
ms.openlocfilehash: 66dba1df125a08b8ae05519a0c66edb6da15ceaa
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583419"
---
# <a name="end-statement"></a>End Deyimi
Yürütmeyi hemen sonlandırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
End  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Tüm uygulamayı çalışmayı durdurmayı zorlamak için `End` ifadesini bir yordamın her yerinden yerleştirebilirsiniz. `End`, `Open` ifadesiyle açılan tüm dosyaları kapatır ve tüm uygulamanın değişkenlerini temizler. Nesneleri, nesnelerine başvuruları tutan başka hiçbir program yoksa ve kodun hiçbiri çalışmıyorsa, uygulama kapanır.  
  
> [!NOTE]
> @No__t_0 ifade kodu yürütmeyi aniden durduruyor ve `Dispose` veya `Finalize` yöntemini ya da başka bir Visual Basic kodu çağırmaz. Diğer programlar tarafından tutulan nesne başvuruları geçersiz kılınır. Bir `Try` veya `Catch` bloğunda `End` ifadesiyle karşılaşılırsa, denetim karşılık gelen `Finally` bloğuna geçmez.  
  
 @No__t_0 deyimin yürütülmesi askıya alınır, ancak `End` aksine, derlenmiş bir çalıştırılabilir (. exe) dosyasında karşılaşılmadığı takdirde hiçbir dosyayı kapatmaz veya hiçbir değişkeni temizlemez.  
  
 @No__t_0, açık olabilecek kaynaklara katılmaksızın uygulamanızı sonlandırdığından, kullanmadan önce düzgün bir şekilde kapatmayı denemeniz gerekir. Örneğin, uygulamanızda açık bir form varsa, denetim `End` bildirimine ulaşmadan önce bunları kapatmanız gerekir.  
  
 @No__t_0 gelişigüzel ve yalnızca hemen durdurmanız gerektiğinde kullanmanız gerekir. Bir yordamı ([Return deyimleri](../../../visual-basic/language-reference/statements/return-statement.md) ve [Exit ifadesini](../../../visual-basic/language-reference/statements/exit-statement.md)) sonlandırmak için normal yollar, yordamı yalnızca düzgün bir şekilde kapatmaz, aynı zamanda çağıran koda düzgün bir şekilde kapatma fırsatı verir. Örneğin, bir konsol uygulaması, `Main` yordamından yalnızca `Return` olabilir.  
  
> [!IMPORTANT]
> @No__t_0 ifade <xref:System> ad alanındaki <xref:System.Environment> sınıfının <xref:System.Environment.Exit%2A> yöntemini çağırır. <xref:System.Environment.Exit%2A> için `UnmanagedCode` izninizin olması gerekir. Bunu yapmazsanız <xref:System.Security.SecurityException> bir hata oluşur.  
  
 Daha sonra ek bir anahtar sözcük olduğunda [End \<keyword > deyimleri](../../../visual-basic/language-reference/statements/end-keyword-statement.md) uygun yordamın veya bloğun tanımının sonuna göre ayırıcıları. Örneğin, `End Function` bir `Function` yordamının tanımını sonlandırır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, Kullanıcı istediğinde kod yürütmeyi sonlandırmak için `End` ifadesini kullanır.  
  
 [!code-vb[VbVersHelp60Controls#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVersHelp60Controls/VB/Form1.vb#64)]  
  
## <a name="smart-device-developer-notes"></a>Akıllı Cihaz Geliştirici Notları  
 Bu ifade desteklenmiyor.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Security.Permissions.SecurityPermissionFlag>
- [Stop Deyimi](../../../visual-basic/language-reference/statements/stop-statement.md)
- [End \<keyword > ekstresi](../../../visual-basic/language-reference/statements/end-keyword-statement.md)
