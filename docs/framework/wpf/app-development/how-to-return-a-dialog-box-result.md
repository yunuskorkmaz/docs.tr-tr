---
title: 'Nasıl yapılır: İletişim Kutusu Sonucu Döndürme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dialog boxes [WPF], returning results
ms.assetid: 4c5cf286-746b-4052-934d-d80cbf8acba3
ms.openlocfilehash: 5e3670006762bcd09634b29314ecf2d05b1a44da
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968240"
---
# <a name="how-to-return-a-dialog-box-result"></a>Nasıl yapılır: İletişim Kutusu Sonucu Döndürme
Bu örnek, çağırarak <xref:System.Windows.Window.ShowDialog%2A>açılan bir pencere için diyalog sonucunun nasıl alınacağını gösterir.  
  
## <a name="example"></a>Örnek  
 İletişim kutusu kapanmadan önce, <xref:System.Windows.Window.DialogResult%2A> özelliği kullanıcının iletişim kutusunu nasıl kapattığını gösteren bir <xref:System.Nullable%601> <xref:System.Boolean> ile ayarlanmalıdır. Bu değer, istemci kodunun <xref:System.Windows.Window.ShowDialog%2A> iletişim kutusunun nasıl kapatıldığını ve sonuç olarak sonucun nasıl işleyeceğini belirlemesine izin vermek için tarafından döndürülür.  
  
> [!NOTE]
> <xref:System.Windows.Window.DialogResult%2A>yalnızca, çağırarak <xref:System.Windows.Window.ShowDialog%2A>bir pencere açılırsa ayarlanabilir.  
  
 [!code-csharp[HOWTOWindowManagementSnippets#GetDialogResultCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#getdialogresultcode)]
 [!code-vb[HOWTOWindowManagementSnippets#GetDialogResultCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#getdialogresultcode)]  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Çağırma <xref:System.Windows.Window.ShowDialog%2A> , tüm Windows ve Kullanıcı giriş olaylarını kısıtlama olmadan kullanma izni gerektirir.
