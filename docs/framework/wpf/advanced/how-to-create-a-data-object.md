---
title: 'Nasıl yapılır: Veri Nesnesi Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataObject class [WPF], creating
- data objects [WPF], creating
- drag-and-drop [WPF], creating data objects
ms.assetid: 022fa142-717d-4fea-a53c-3b52e9d91aff
ms.openlocfilehash: f7bdfbf3dba0c700513348195c1d031d4c2c8b65
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57370598"
---
# <a name="how-to-create-a-data-object"></a><span data-ttu-id="88ac9-102">Nasıl yapılır: Veri Nesnesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="88ac9-102">How to: Create a Data Object</span></span>
<span data-ttu-id="88ac9-103">Aşağıdaki örnekler tarafından sağlanan oluşturucuları kullanarak bir veri nesnesi oluşturmak için çeşitli yollar <xref:System.Windows.DataObject> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="88ac9-103">The following examples show various ways to create a data object using the constructors provided by the <xref:System.Windows.DataObject> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88ac9-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="88ac9-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="88ac9-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="88ac9-105">Description</span></span>  
 <span data-ttu-id="88ac9-106">Aşağıdaki kod örneği, yeni bir veri nesnesi oluşturur ve aşırı yüklü oluşturucular birini kullanır (<xref:System.Windows.DataObject.%23ctor%28System.Object%29>) veri nesnesinin bir dize ile başlatılamadı.</span><span class="sxs-lookup"><span data-stu-id="88ac9-106">The following example code creates a new data object and uses one of the overloaded constructors (<xref:System.Windows.DataObject.%23ctor%28System.Object%29>) to initialize the data object with a string.</span></span>  <span data-ttu-id="88ac9-107">Bu durumda, uygun veri biçimi otomatik olarak saklanan veri türüne göre belirlenir ve otomatik dönüştürme, depolanan verilerin varsayılan olarak izin verilir.</span><span class="sxs-lookup"><span data-stu-id="88ac9-107">In this case, an appropriate data format is determined automatically according to the stored data's type, and auto-converting of the stored data is allowed by default.</span></span>  
  
### <a name="code"></a><span data-ttu-id="88ac9-108">Kod</span><span class="sxs-lookup"><span data-stu-id="88ac9-108">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Simple](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_simple)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Simple](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_simple)]  
  
### <a name="description"></a><span data-ttu-id="88ac9-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="88ac9-109">Description</span></span>  
 <span data-ttu-id="88ac9-110">Aşağıdaki kod örneği, yukarıda gösterilen koddan sıkıştırılmış bir sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="88ac9-110">The following example code is a condensed version of the code shown above.</span></span>  
  
### <a name="code"></a><span data-ttu-id="88ac9-111">Kod</span><span class="sxs-lookup"><span data-stu-id="88ac9-111">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Simple_Condensed](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_simple_condensed)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Simple_Condensed](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_simple_condensed)]  
  
## <a name="example"></a><span data-ttu-id="88ac9-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="88ac9-112">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="88ac9-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="88ac9-113">Description</span></span>  
 <span data-ttu-id="88ac9-114">Aşağıdaki kod örneği, yeni bir veri nesnesi oluşturur ve aşırı yüklü oluşturucular birini kullanır (<xref:System.Windows.DataObject.%23ctor%28System.String%2CSystem.Object%29>) veri nesnesinin bir dize ve belirtilen veri biçimi ile başlatılamadı.</span><span class="sxs-lookup"><span data-stu-id="88ac9-114">The following example code creates a new data object and uses one of the overloaded constructors (<xref:System.Windows.DataObject.%23ctor%28System.String%2CSystem.Object%29>) to initialize the data object with a string and a specified data format.</span></span>  <span data-ttu-id="88ac9-115">Bu durumda veri biçimi dizesi tarafından belirtilen; <xref:System.Windows.DataFormats> sınıfı bir dizi önceden tanımlanmış türü dizesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="88ac9-115">In this case the data format is specified by a string; the <xref:System.Windows.DataFormats> class provides a set of pre-defined type strings.</span></span> <span data-ttu-id="88ac9-116">Otomatik dönüştürme, depolanan verilerin varsayılan olarak izin verilir.</span><span class="sxs-lookup"><span data-stu-id="88ac9-116">Auto-converting of the stored data is allowed by default.</span></span>  
  
### <a name="code"></a><span data-ttu-id="88ac9-117">Kod</span><span class="sxs-lookup"><span data-stu-id="88ac9-117">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_typestring)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_typestring)]  
  
### <a name="description"></a><span data-ttu-id="88ac9-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="88ac9-118">Description</span></span>  
 <span data-ttu-id="88ac9-119">Aşağıdaki kod örneği, yukarıda gösterilen koddan sıkıştırılmış bir sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="88ac9-119">The following example code is a condensed version of the code shown above.</span></span>  
  
### <a name="code"></a><span data-ttu-id="88ac9-120">Kod</span><span class="sxs-lookup"><span data-stu-id="88ac9-120">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString_Condensed](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_typestring_condensed)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString_Condensed](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_typestring_condensed)]  
  
## <a name="example"></a><span data-ttu-id="88ac9-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="88ac9-121">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="88ac9-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="88ac9-122">Description</span></span>  
 <span data-ttu-id="88ac9-123">Aşağıdaki kod örneği, yeni bir veri nesnesi oluşturur ve aşırı yüklü oluşturucular birini kullanır (<xref:System.Windows.DataObject.%23ctor%2A>) veri nesnesinin bir dize ve belirtilen veri biçimi ile başlatılamadı.</span><span class="sxs-lookup"><span data-stu-id="88ac9-123">The following example code creates a new data object and uses one of the overloaded constructors (<xref:System.Windows.DataObject.%23ctor%2A>) to initialize the data object with a string and a specified data format.</span></span>  <span data-ttu-id="88ac9-124">Bu durumda veri biçimi tarafından belirtilen bir <xref:System.Type> parametresi.</span><span class="sxs-lookup"><span data-stu-id="88ac9-124">In this case the data format is specified by a <xref:System.Type> parameter.</span></span>  <span data-ttu-id="88ac9-125">Otomatik dönüştürme, depolanan verilerin varsayılan olarak izin verilir.</span><span class="sxs-lookup"><span data-stu-id="88ac9-125">Auto-converting of the stored data is allowed by default.</span></span>  
  
### <a name="code"></a><span data-ttu-id="88ac9-126">Kod</span><span class="sxs-lookup"><span data-stu-id="88ac9-126">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Type](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_type)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Type](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_type)]  
  
### <a name="description"></a><span data-ttu-id="88ac9-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="88ac9-127">Description</span></span>  
 <span data-ttu-id="88ac9-128">Aşağıdaki kod örneği, yukarıda gösterilen koddan sıkıştırılmış bir sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="88ac9-128">The following example code is a condensed version of the code shown above.</span></span>  
  
### <a name="code"></a><span data-ttu-id="88ac9-129">Kod</span><span class="sxs-lookup"><span data-stu-id="88ac9-129">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Type_Condensed](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_type_condensed)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Type_Condensed](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_type_condensed)]  
  
## <a name="example"></a><span data-ttu-id="88ac9-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="88ac9-130">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="88ac9-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="88ac9-131">Description</span></span>  
 <span data-ttu-id="88ac9-132">Aşağıdaki kod örneği, yeni bir veri nesnesi oluşturur ve aşırı yüklü oluşturucular birini kullanır (<xref:System.Windows.DataObject.%23ctor%28System.String%2CSystem.Object%2CSystem.Boolean%29>) veri nesnesinin bir dize ve belirtilen veri biçimi ile başlatılamadı.</span><span class="sxs-lookup"><span data-stu-id="88ac9-132">The following example code creates a new data object and uses one of the overloaded constructors (<xref:System.Windows.DataObject.%23ctor%28System.String%2CSystem.Object%2CSystem.Boolean%29>) to initialize the data object with a string and a specified data format.</span></span>  <span data-ttu-id="88ac9-133">Bu durumda veri biçimi dizesi tarafından belirtilen; <xref:System.Windows.DataFormats> sınıfı bir dizi önceden tanımlanmış türü dizesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="88ac9-133">In this case the data format is specified by a string; the <xref:System.Windows.DataFormats> class provides a set of pre-defined type strings.</span></span> <span data-ttu-id="88ac9-134">Bu belirli kurucu aşırı yükleme, otomatik dönüştürme izin verilip verilmeyeceğini belirtmek çağıranın sağlar.</span><span class="sxs-lookup"><span data-stu-id="88ac9-134">This particular constructor overload enables the caller to specify whether auto-converting is allowed.</span></span>  
  
### <a name="code"></a><span data-ttu-id="88ac9-135">Kod</span><span class="sxs-lookup"><span data-stu-id="88ac9-135">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_AutoConvert](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_autoconvert)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_AutoConvert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_autoconvert)]  
  
### <a name="description"></a><span data-ttu-id="88ac9-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="88ac9-136">Description</span></span>  
 <span data-ttu-id="88ac9-137">Aşağıdaki kod örneği, yukarıda gösterilen koddan sıkıştırılmış bir sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="88ac9-137">The following example code is a condensed version of the code shown above.</span></span>  
  
### <a name="code"></a><span data-ttu-id="88ac9-138">Kod</span><span class="sxs-lookup"><span data-stu-id="88ac9-138">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_AutoConvert_Condensed](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_autoconvert_condensed)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_AutoConvert_Condensed](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_autoconvert_condensed)]  
  
## <a name="see-also"></a><span data-ttu-id="88ac9-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="88ac9-139">See also</span></span>
- <xref:System.Windows.IDataObject>
