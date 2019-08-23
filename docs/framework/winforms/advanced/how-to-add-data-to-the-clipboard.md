---
title: 'Nasıl yapılır: Panoya Veri Ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Clipboard [Windows Forms], copying data to
- data [Windows Forms], copying to Clipboard
ms.assetid: 25152454-0e78-40a9-8a9e-a2a5a274e517
ms.openlocfilehash: d4afcd6ce942d1cd2286e3f393ce61436821bb3a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955120"
---
# <a name="how-to-add-data-to-the-clipboard"></a>Nasıl yapılır: Panoya Veri Ekleme
Sınıfı <xref:System.Windows.Forms.Clipboard> , Windows işletim sistemi Pano özelliğiyle etkileşim kurmak için kullanabileceğiniz yöntemler sağlar. Birçok uygulama, pano 'Yu veri için geçici bir depo olarak kullanır. Örneğin, Word işlemcileri kes ve yapıştır işlemleri sırasında panoyu kullanır. Pano, verileri bir uygulamadan diğerine aktarmak için de kullanışlıdır.  
  
 Panoya veri eklediğinizde, diğer uygulamaların bu biçimi kullanabilmesi durumunda verileri tanıyabilmesi için veri biçimini belirtebilirsiniz. Ayrıca, verileri potansiyel olarak kullanbilecek diğer uygulamaların sayısını artırmak için birden çok farklı biçimde panoya veri ekleyebilirsiniz.  
  
 Pano biçimi, bu biçimi kullanan bir uygulamanın ilişkili verileri alabilmesi için biçimi tanımlayan bir dizedir. Sınıfı <xref:System.Windows.Forms.DataFormats> , kullanım için önceden tanımlanmış biçim adları sağlar. Kendi biçim adlarınızı de kullanabilir veya bir nesnenin türünü biçimi olarak kullanabilirsiniz.  
  
 Panoya bir veya birden çok biçimde veri eklemek için <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> yöntemini kullanın. Bu yönteme herhangi bir nesne geçirebilirsiniz, ancak birden fazla formatta veri eklemek için, önce verileri birden çok biçim ile çalışacak şekilde tasarlanan ayrı bir nesneye eklemeniz gerekir. Genellikle verilerinizi bir <xref:System.Windows.Forms.DataObject>öğesine eklersiniz, ancak <xref:System.Windows.Forms.IDataObject> arabirimi uygulayan herhangi bir türü kullanabilirsiniz.  
  
 .NET Framework 2,0 ' de, temel Pano görevlerini daha kolay hale getirmek için tasarlanan yeni yöntemleri kullanarak doğrudan panoya veri ekleyebilirsiniz. Verilerle birlikte çalışırken, metin gibi tek bir ortak biçimdeki bu yöntemleri kullanın.  
  
> [!NOTE]
> Tüm Windows tabanlı uygulamalar panoyu paylaşır. Bu nedenle, başka bir uygulamaya geçtiğinizde içerik değişebilir.  
>   
>  <xref:System.Windows.Forms.Clipboard> Sınıfı yalnızca tek iş parçacığı apartmanı (STA) moduna ayarlanmış iş parçacıklarında kullanılabilir. Bu sınıfı kullanmak için `Main` yönteminizin <xref:System.STAThreadAttribute> özniteliğiyle işaretlendiğinden emin olun.  
>   
>  Bir nesne, pano 'Ya yerleştirilecek şekilde seri hale getirilebilir olmalıdır. Bir türü seri hale getirilebilir yapmak için <xref:System.SerializableAttribute> özniteliğiyle işaretleyin. Bir pano yöntemine serileştirilebilir olmayan bir nesne geçirirseniz, yöntem özel durum oluşturmadan başarısız olur. Serileştirme hakkında daha fazla bilgi için bkz <xref:System.Runtime.Serialization>.  
  
### <a name="to-add-data-to-the-clipboard-in-a-single-common-format"></a>Tek, ortak bir biçimde panoya veri eklemek için  
  
1. ,, Veya metodunu<xref:System.Windows.Forms.Clipboard.SetText%2A> kullanın. <xref:System.Windows.Forms.Clipboard.SetFileDropList%2A> <xref:System.Windows.Forms.Clipboard.SetAudio%2A> <xref:System.Windows.Forms.Clipboard.SetImage%2A> Bu yöntemler yalnızca .NET Framework 2,0 ' de kullanılabilir.  
  
     [!code-csharp[System.Windows.Forms.Clipboard#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.Clipboard#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#2)]  
  
### <a name="to-add-data-to-the-clipboard-in-a-custom-format"></a>Panoya özel bir biçimde veri eklemek için  
  
1. <xref:System.Windows.Forms.Clipboard.SetData%2A> Yöntemi özel biçim adıyla kullanın. Bu yöntem yalnızca .NET Framework 2,0 ' de kullanılabilir.  
  
     Önceden tanımlanmış biçim adlarını <xref:System.Windows.Forms.Clipboard.SetData%2A> yöntemiyle de kullanabilirsiniz. Daha fazla bilgi için bkz. <xref:System.Windows.Forms.DataFormats>.  
  
     [!code-csharp[System.Windows.Forms.Clipboard#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.Clipboard#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#3)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
### <a name="to-add-data-to-the-clipboard-in-multiple-formats"></a>Birden çok biçimdeki panoya veri eklemek için  
  
1. Yöntemini kullanın ve verilerinizi içeren bir <xref:System.Windows.Forms.DataObject> içinde geçiş yapın. <xref:System.Windows.Forms.Clipboard.SetDataObject%2A?displayProperty=nameWithType> .NET Framework 2,0 ' den önceki sürümlerde Pano 'ya veri eklemek için bu yöntemi kullanmanız gerekir.  
  
     [!code-csharp[System.Windows.Forms.Clipboard#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.Clipboard#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#4)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sürükle ve Bırak İşlemleri ve Pano Desteği](drag-and-drop-operations-and-clipboard-support.md)
- [Nasıl yapılır: Panodan veri alma](how-to-retrieve-data-from-the-clipboard.md)
