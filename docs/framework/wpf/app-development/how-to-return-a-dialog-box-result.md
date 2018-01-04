---
title: "Nasıl yapılır: bir iletişim kutusu sonucunu döndürür"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: dialog boxes [WPF], returning results
ms.assetid: 4c5cf286-746b-4052-934d-d80cbf8acba3
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5f8133ffa7be9cb4e0600fc2681402d5e0f7471c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-return-a-dialog-box-result"></a>Nasıl yapılır: bir iletişim kutusu sonucunu döndürür
Bu örnek çağırarak açılan bir pencere için iletişim sonucu almak nasıl gösterir <xref:System.Windows.Window.ShowDialog%2A>.  
  
## <a name="example"></a>Örnek  
 Bir iletişim kutusu kapanmadan önce kendi <xref:System.Windows.Window.DialogResult%2A> özelliği ile ayarlanmalıdır bir <xref:System.Nullable%601> <xref:System.Boolean> nasıl kullanıcı iletişim kutusu kapalı gösterir. Bu değer tarafından döndürülen <xref:System.Windows.Window.ShowDialog%2A> iletişim kutusunun nasıl kapatıldığını ve sonuç olarak, sonucu işle nasıl belirlemek istemci kodu izin vermek için.  
  
> [!NOTE]
>  <xref:System.Windows.Window.DialogResult%2A>yalnızca bir pencere çağırarak açıldıysa ayarlanabilir <xref:System.Windows.Window.ShowDialog%2A>.  
  
 [!code-csharp[HOWTOWindowManagementSnippets#GetDialogResultCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#getdialogresultcode)]
 [!code-vb[HOWTOWindowManagementSnippets#GetDialogResultCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#getdialogresultcode)]  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Çağırma <xref:System.Windows.Window.ShowDialog%2A> tüm windows ve kullanıcı girdi olaylarını kısıtlama olmaksızın kullanma izni gerektirir.
