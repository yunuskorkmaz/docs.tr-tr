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
ms.openlocfilehash: fe17a82662c4014069c77f2da76723a051ab9084
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404712"
---
# <a name="end-statement"></a>End Deyimi
Yürütmeyi hemen sonlandırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
End  
```  
  
## <a name="remarks"></a>Açıklamalar  
 `End`Tüm uygulamayı çalışmayı durdurmayı zorlamak için ifadeyi bir yordamda herhangi bir yere yerleştirebilirsiniz. `End`ifadesiyle açılan tüm dosyaları kapatır `Open` ve tüm uygulamanın değişkenlerini temizler. Nesneleri, nesnelerine başvuruları tutan başka hiçbir program yoksa ve kodun hiçbiri çalışmıyorsa, uygulama kapanır.  
  
> [!NOTE]
> `End`İfade kod yürütmeyi aniden durduruyor ve ya da metodunu ya da `Dispose` `Finalize` başka bir Visual Basic kodunu çağırmaz. Diğer programlar tarafından tutulan nesne başvuruları geçersiz kılınır. `End`Bir veya bloğu içinde bir ifadeye karşılaşılırsa `Try` `Catch` , denetim karşılık gelen bloğa geçmez `Finally` .  
  
 `Stop`İfade yürütmeyi askıya alır, ancak farklı olarak, `End` derlenmiş bir çalıştırılabilir (. exe) dosyasında karşılaşılmadığı takdirde herhangi bir dosyayı kapatmaz veya hiçbir değişkeni temizlemez.  
  
 `End`Açık olabilecek kaynaklara katılmadan uygulamanızı sonlandırdığından, kullanmadan önce düzgün bir şekilde kapatmayı denemeniz gerekir. Örneğin, uygulamanızda açık bir form varsa, denetim ifadeye ulaşmadan önce bunları kapatmalısınız `End` .  
  
 `End`Gelişigüzel ve yalnızca hemen durdurmanız gerektiğinde kullanmanız gerekir. Bir yordamı ([Return deyimleri](return-statement.md) ve [Exit ifadesini](exit-statement.md)) sonlandırmak için normal yollar, yordamı yalnızca düzgün bir şekilde kapatmaz, aynı zamanda çağıran koda düzgün bir şekilde kapatma fırsatı verir. Örneğin, bir konsol uygulaması yalnızca `Return` `Main` yordamdan olabilir.  
  
> [!IMPORTANT]
> `End`İfade, <xref:System.Environment.Exit%2A> <xref:System.Environment> ad alanındaki sınıfının yöntemini çağırır <xref:System> . <xref:System.Environment.Exit%2A>izninizin olması gerekir `UnmanagedCode` . Aksi takdirde bir <xref:System.Security.SecurityException> hata oluşur.  
  
 Ardından ek bir anahtar sözcük geldiğinde, [End \<keyword> ifadesinin](end-keyword-statement.md) uygun yordam veya bloğun tanımının sonuna göre tanımlanması gerekir. Örneğin, `End Function` bir yordamın tanımını sonlandırır `Function` .  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `End` Kullanıcı istediğinde kod yürütmeyi sonlandırmak için ifadesini kullanır.  
  
 [!code-vb[VbVersHelp60Controls#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVersHelp60Controls/VB/Form1.vb#64)]  
  
## <a name="smart-device-developer-notes"></a>Akıllı Cihaz Geliştirici Notları  
 Bu ifade desteklenmiyor.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Security.Permissions.SecurityPermissionFlag>
- [Stop Deyimi](stop-statement.md)
- [End \<keyword> ekstresi](end-keyword-statement.md)
