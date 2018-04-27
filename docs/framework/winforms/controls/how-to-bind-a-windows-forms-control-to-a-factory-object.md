---
title: 'Nasıl yapılır: Windows Forms Denetimini Bir Fabrika Nesnesine Bağlama'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], binding
- factory objects [Windows Forms], binding to
- BindingSource component [Windows Forms], binding to a factory object
- BindingSource component [Windows Forms], examples
ms.assetid: 7d59af89-ff82-41d8-a48a-f1fbae788b0d
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a5df2cd4601f2099c9c1d8a0075bdc6043bb2cd0
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-bind-a-windows-forms-control-to-a-factory-object"></a>Nasıl yapılır: Windows Forms Denetimini Bir Fabrika Nesnesine Bağlama
Verilerle etkileşimli denetimleri oluştururken, bazen, bir denetim için bir nesne veya diğer nesnelerini oluşturan yöntem bağlamak gerekli bulacaksınız. Bu tür bir nesneye veya yöntemi bir Fabrika adı verilir. Veri kaynağı, örneğin, bellek veya bir türü bir nesne yerine bir yöntem çağrısının dönüş değerini olabilir. Kaynak bir koleksiyon döndürür sürece bu türdeki veri kaynağının bir denetim bağlayabilirsiniz.  
  
 Kullanarak bir denetimi Fabrika nesnesine kolayca bağlayabilirsiniz <xref:System.Windows.Forms.BindingSource> denetim.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte nasıl bağlanacağını gösterir bir <xref:System.Windows.Forms.DataGridView> kullanarak bir Üreteç yöntemi denetimine bir <xref:System.Windows.Forms.BindingSource> denetim. Üreteç yöntemi adlı `GetOrdersByCustomerId`, ve belirli bir müşteri için tüm siparişleri Northwind veritabanına döndürür.  
  
 [!code-cpp[System.Windows.Forms.DataConnector.BindToFactory#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.BindToFactory#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.BindToFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Sistem, System.Data, System.Drawing ve System.Windows.Forms derlemelerine başvurular.  
  
 Visual Basic veya Visual C# için bu örnek komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Bu örnek ayrıca oluşturmak [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] yeni bir proje kodunu yapıştırma tarafından.  Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.BindingNavigator>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [BindingSource Bileşeni](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [Nasıl yapılır: Windows Forms Denetimini Bir Türe Bağlama](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)
