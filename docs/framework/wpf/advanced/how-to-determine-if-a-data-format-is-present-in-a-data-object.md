---
title: 'Nasıl yapılır: Veri Nesnesinde Veri Biçiminin Olup Olmadığını Belirleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataFormats class [WPF]
- drag-and-drop [WPF], data formats present
- data formats [WPF], determining if present
ms.assetid: e487a454-c9fc-4e53-aeaa-c458d059ad4c
ms.openlocfilehash: 57190b94988c8ee557e99836a8e8500bfb622f2e
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57379178"
---
# <a name="how-to-determine-if-a-data-format-is-present-in-a-data-object"></a><span data-ttu-id="328e6-102">Nasıl yapılır: Veri Nesnesinde Veri Biçiminin Olup Olmadığını Belirleme</span><span class="sxs-lookup"><span data-stu-id="328e6-102">How to: Determine if a Data Format is Present in a Data Object</span></span>
<span data-ttu-id="328e6-103">Aşağıdaki örnekler çeşitli kullanmayı <xref:System.Windows.DataObject.GetDataPresent%2A> yöntemi belirli veri biçiminde veri nesnesinde var olup olmadığını sorgulamak için aşırı yüklemeleri.</span><span class="sxs-lookup"><span data-stu-id="328e6-103">The following examples show how to use the various <xref:System.Windows.DataObject.GetDataPresent%2A> method overloads to query whether a particular data format is present in a data object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="328e6-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="328e6-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="328e6-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="328e6-105">Description</span></span>  
 <span data-ttu-id="328e6-106">Aşağıdaki örnek kod <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> aşırı yükleme tanımlayıcısı dizesindeki bir belirli veri biçiminde varlığını sorgulanamıyor.</span><span class="sxs-lookup"><span data-stu-id="328e6-106">The following example code uses the <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> overload to query for the presence of a particular data format by descriptor string.</span></span>  
  
### <a name="code"></a><span data-ttu-id="328e6-107">Kod</span><span class="sxs-lookup"><span data-stu-id="328e6-107">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_String](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_querydataformats_string)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_String](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_querydataformats_string)]  
  
## <a name="example"></a><span data-ttu-id="328e6-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="328e6-108">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="328e6-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="328e6-109">Description</span></span>  
 <span data-ttu-id="328e6-110">Aşağıdaki örnek kod <xref:System.Windows.DataObject.GetDataPresent%28System.Type%29> sorgu varlığını türüne göre belirli veri biçimi için aşırı yükleme.</span><span class="sxs-lookup"><span data-stu-id="328e6-110">The following example code uses the <xref:System.Windows.DataObject.GetDataPresent%28System.Type%29> overload to query for the presence of a particular data format by type.</span></span>  
  
### <a name="code"></a><span data-ttu-id="328e6-111">Kod</span><span class="sxs-lookup"><span data-stu-id="328e6-111">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Type](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_querydataformats_type)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Type](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_querydataformats_type)]  
  
## <a name="example"></a><span data-ttu-id="328e6-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="328e6-112">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="328e6-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="328e6-113">Description</span></span>  
 <span data-ttu-id="328e6-114">Aşağıdaki örnek kod <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> tanımlayıcı dizesi tarafından aşırı sorgulamak için veri ve nasıl işlemesi gerektiğini otomatik dönüştürülebilir veri biçimleri belirleme.</span><span class="sxs-lookup"><span data-stu-id="328e6-114">The following example code uses the <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> overload to query for data by descriptor string, and specifying how to treat auto-convertible data formats.</span></span>  
  
### <a name="code"></a><span data-ttu-id="328e6-115">Kod</span><span class="sxs-lookup"><span data-stu-id="328e6-115">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Autoconvert](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_querydataformats_autoconvert)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Autoconvert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_querydataformats_autoconvert)]  
  
## <a name="see-also"></a><span data-ttu-id="328e6-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="328e6-116">See also</span></span>
- <xref:System.Windows.IDataObject>
