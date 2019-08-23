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
ms.openlocfilehash: 9307cf10e6125441bd49baa0e663a5a13f234005
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944460"
---
# <a name="end-statement"></a>End Deyimi
Yürütmeyi hemen sonlandırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
End  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Tüm uygulamayı çalışmayı durdurmayı `End` zorlamak için ifadeyi bir yordamda herhangi bir yere yerleştirebilirsiniz. `End``Open` ifadesiyle açılan tüm dosyaları kapatır ve tüm uygulamanın değişkenlerini temizler. Nesneleri, nesnelerine başvuruları tutan başka hiçbir program yoksa ve kodun hiçbiri çalışmıyorsa, uygulama kapanır.  
  
> [!NOTE]
> İfade kod yürütmeyi aniden durduruyor ve `Dispose` ya `Finalize` da metodunu ya da başka bir Visual Basic kodunu çağırmaz. `End` Diğer programlar tarafından tutulan nesne başvuruları geçersiz kılınır. Bir `End` `Finally` veya bloğu`Catch` içinde bir ifadeye karşılaşılırsa, denetim karşılık gelen bloğa geçmez. `Try`  
  
 İfade yürütmeyi askıya alır, ancak farklı `End`olarak, derlenmiş bir çalıştırılabilir (. exe) dosyasında karşılaşılmadığı takdirde herhangi bir dosyayı kapatmaz veya hiçbir değişkeni temizlemez. `Stop`  
  
 Açık `End` olabilecek kaynaklara katılmadan uygulamanızı sonlandırdığından, kullanmadan önce düzgün bir şekilde kapatmayı denemeniz gerekir. Örneğin, uygulamanızda açık bir form varsa, Denetim `End` ifadeye ulaşmadan önce bunları kapatmalısınız.  
  
 Gelişigüzel ve yalnızca `End` hemen durdurmanız gerektiğinde kullanmanız gerekir. Bir yordamı ([Return deyimleri](../../../visual-basic/language-reference/statements/return-statement.md) ve [Exit ifadesini](../../../visual-basic/language-reference/statements/exit-statement.md)) sonlandırmak için normal yollar, yordamı yalnızca düzgün bir şekilde kapatmaz, aynı zamanda çağıran koda düzgün bir şekilde kapatma fırsatı verir. Örneğin, bir konsol uygulaması yalnızca `Return` `Main` yordamdan olabilir.  
  
> [!IMPORTANT]
> İfade, <xref:System.Environment.Exit%2A> <xref:System.Environment> ad alanındaki sınıfının yöntemini çağırır. <xref:System> `End` <xref:System.Environment.Exit%2A>izninizin olması `UnmanagedCode` gerekir. Aksi takdirde bir <xref:System.Security.SecurityException> hata oluşur.  
  
 Sonrasında ek bir anahtar sözcük, [End \<anahtar sözcüğü > deyimin](../../../visual-basic/language-reference/statements/end-keyword-statement.md) uygun yordam veya bloğun tanımının sonuna göre ayırıcıları. Örneğin, `End Function` bir `Function` yordamın tanımını sonlandırır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, Kullanıcı istediğinde `End` kod yürütmeyi sonlandırmak için ifadesini kullanır.  
  
 [!code-vb[VbVersHelp60Controls#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVersHelp60Controls/VB/Form1.vb#64)]  
  
## <a name="smart-device-developer-notes"></a>Akıllı Cihaz Geliştirici Notları  
 Bu ifade desteklenmiyor.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Security.Permissions.SecurityPermissionFlag>
- [Stop Deyimi](../../../visual-basic/language-reference/statements/stop-statement.md)
- [End \<anahtar sözcüğü > ekstresi](../../../visual-basic/language-reference/statements/end-keyword-statement.md)
