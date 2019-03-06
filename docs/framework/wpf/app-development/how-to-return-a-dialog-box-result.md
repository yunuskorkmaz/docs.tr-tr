---
title: 'Nasıl yapılır: Bir iletişim kutusu sonucu döndürme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dialog boxes [WPF], returning results
ms.assetid: 4c5cf286-746b-4052-934d-d80cbf8acba3
ms.openlocfilehash: b574a5bbc08d947371837116915c2fc8c13ec81d
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57357774"
---
# <a name="how-to-return-a-dialog-box-result"></a>Nasıl yapılır: Bir iletişim kutusu sonucu döndürme
Bu örnekte, iletişim sonucu çağırarak açılan bir pencere için alma işlemi gösterilmektedir <xref:System.Windows.Window.ShowDialog%2A>.  
  
## <a name="example"></a>Örnek  
 Bir iletişim kutusu kapanır önce kendi <xref:System.Windows.Window.DialogResult%2A> özelliği ile ayarlanmalıdır bir <xref:System.Nullable%601> <xref:System.Boolean> nasıl kullanıcı iletişim kutusu kapalıyken gösterir. Bu değer tarafından döndürülür <xref:System.Windows.Window.ShowDialog%2A> iletişim kutusu nasıl kapatıldığı ve sonuç olarak, sonuç işlemek nasıl belirlemek istemci kodu izin vermek için.  
  
> [!NOTE]
>  <xref:System.Windows.Window.DialogResult%2A> bir pencere çağırarak açıldıysa ayarlanabilir <xref:System.Windows.Window.ShowDialog%2A>.  
  
 [!code-csharp[HOWTOWindowManagementSnippets#GetDialogResultCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#getdialogresultcode)]
 [!code-vb[HOWTOWindowManagementSnippets#GetDialogResultCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#getdialogresultcode)]  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Çağırma <xref:System.Windows.Window.ShowDialog%2A> tüm windows ve kısıtlama olmaksızın kullanıcı girdi olaylarını kullanma izni gerektirir.
