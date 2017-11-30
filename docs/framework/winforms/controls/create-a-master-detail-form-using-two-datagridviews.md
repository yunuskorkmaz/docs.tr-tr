---
title: "Nasıl yapılır: iki Windows Forms DataGridView denetimi kullanarak ana / ayrıntı formu oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], master/detail form
- parent-child tables [Windows Forms], displaying on Windows Forms
- master-details lists [Windows Forms], creating
ms.assetid: 99f6e876-3f7f-4139-9063-e36587c95b02
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0b18e26ff20496248e4525bc31722cf6fcbbc3da
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-masterdetail-form-using-two-windows-forms-datagridview-controls"></a>Nasıl Yapılır: İki Windows Forms DataGridView Denetimi Kullanarak Ana/Ayrıntı Formu Oluşturma
Aşağıdaki kod örneği iki kullanarak ana/ayrıntı formu oluşturur <xref:System.Windows.Forms.DataGridView> iki bağlama denetimleri <xref:System.Windows.Forms.BindingSource> bileşenleri. Veri kaynağı bir <xref:System.Data.DataSet> içeren `Customers` ve `Orders` ile birlikte Northwind SQL Server örnek veritabanındaki tablolar bir <xref:System.Data.DataRelation> aracılığıyla iki ilişkili `CustomerID` sütun.  
  
 Bir <xref:System.Windows.Forms.BindingSource> üst öğeye bağlı `Customers` veri kümesindeki tablo. Bu veriler master görüntülenir <xref:System.Windows.Forms.DataGridView> denetim. Diğer <xref:System.Windows.Forms.BindingSource> ilk veri bağlayıcısı bağlıdır. <xref:System.Windows.Forms.BindingSource.DataMember%2A> İkinci özelliğinin <xref:System.Windows.Forms.BindingSource> ayarlanır <xref:System.Data.DataRelation> adı. Bu ilişkili ayrıntı neden <xref:System.Windows.Forms.DataGridView> alt satırları görüntülemek için Denetim `Orders` asıl geçerli satırda karşılık tablo <xref:System.Windows.Forms.DataGridView> denetim.  
  
 Bu kod örneği tam bir açıklaması için bkz: [izlenecek yol: bir ana öğe/ayrıntı formu kullanarak iki Windows Forms DataGridView denetimi oluşturma](../../../../docs/framework/winforms/controls/creating-a-master-detail-form-using-two-datagridviews.md).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#00)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
 Sistem, System.Data, System.Windows.Forms ve System.XML derlemelerine başvurular.  
  
 Bu örnek için komut satırından oluşturma hakkında bilgi için [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] veya [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Bu örnek ayrıca oluşturmak [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] yeni bir proje kodunu yapıştırma tarafından.  Ayrıca bkz. [nasıl yapılır: derleme ve bir tam Windows Forms kod örneği kullanarak Visual Studio çalıştırma](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Bağlantı dizesindeki bir parola gibi hassas bilgileri depolamak, uygulamanızın güvenliğini etkileyebilir. Windows Kimlik Doğrulaması (tümleşik güvenlik olarak da bilinir) kullanılarak bir veritabanına erişimi denetlemek için daha güvenli bir yoldur. Daha fazla bilgi için bkz: [koruma bağlantı bilgilerini](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [İzlenecek yol: İki Windows Forms DataGridView denetimi kullanarak ana/ayrıntı formu oluşturma](../../../../docs/framework/winforms/controls/creating-a-master-detail-form-using-two-datagridviews.md)  
 [Windows Forms DataGridView denetiminde verileri görüntüleme](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [Bağlantı bilgileri koruma](../../../../docs/framework/data/adonet/protecting-connection-information.md)
