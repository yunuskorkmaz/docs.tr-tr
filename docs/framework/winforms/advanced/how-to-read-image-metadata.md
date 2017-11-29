---
title: "Nasıl yapılır: Görüntü Meta Verilerini Okuma"
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
- metadata [Windows Forms], property item
- metadata [Windows Forms], reading image
ms.assetid: 72ec0b31-0be7-444a-9575-1dbcb864e0be
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9df2866251e08b8989f8550d045b587c9de8d2cb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-image-metadata"></a><span data-ttu-id="f943e-102">Nasıl yapılır: Görüntü Meta Verilerini Okuma</span><span class="sxs-lookup"><span data-stu-id="f943e-102">How to: Read Image Metadata</span></span>
<span data-ttu-id="f943e-103">Bazı resim dosyaları görüntü özelliklerini belirlemek için okuyabilir meta veriler içerir.</span><span class="sxs-lookup"><span data-stu-id="f943e-103">Some image files contain metadata that you can read to determine features of the image.</span></span> <span data-ttu-id="f943e-104">Örneğin, dijital bir fotoğraf marka ve model görüntüsünü yakalamak için kullanılan kamera belirlemek için okuyabilir meta verileri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="f943e-104">For example, a digital photograph might contain metadata that you can read to determine the make and model of the camera used to capture the image.</span></span> <span data-ttu-id="f943e-105">İle [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], var olan meta verileri okuyabilir ve resim dosyaları için yeni meta verileri de yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f943e-105">With [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], you can read existing metadata, and you can also write new metadata to image files.</span></span>  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="f943e-106">meta verilerde tek bir parçasını depolayan bir <xref:System.Drawing.Imaging.PropertyItem> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="f943e-106"> stores an individual piece of metadata in a <xref:System.Drawing.Imaging.PropertyItem> object.</span></span> <span data-ttu-id="f943e-107">Okuyabilirsiniz <xref:System.Drawing.Image.PropertyItems%2A> özelliği bir <xref:System.Drawing.Image> bir dosyanın tüm meta verilerini almak için nesne.</span><span class="sxs-lookup"><span data-stu-id="f943e-107">You can read the <xref:System.Drawing.Image.PropertyItems%2A> property of an <xref:System.Drawing.Image> object to retrieve all the metadata from a file.</span></span> <span data-ttu-id="f943e-108"><xref:System.Drawing.Image.PropertyItems%2A> Özelliği bir dizi döndürür <xref:System.Drawing.Imaging.PropertyItem> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="f943e-108">The <xref:System.Drawing.Image.PropertyItems%2A> property returns an array of <xref:System.Drawing.Imaging.PropertyItem> objects.</span></span>  
  
 <span data-ttu-id="f943e-109">A <xref:System.Drawing.Imaging.PropertyItem> nesnesi aşağıdaki dört özelliklere sahiptir: `Id`, `Value`, `Len`, ve `Type`.</span><span class="sxs-lookup"><span data-stu-id="f943e-109">A <xref:System.Drawing.Imaging.PropertyItem> object has the following four properties: `Id`, `Value`, `Len`, and `Type`.</span></span>  
  
## <a name="id"></a><span data-ttu-id="f943e-110">Kimliği</span><span class="sxs-lookup"><span data-stu-id="f943e-110">Id</span></span>  
 <span data-ttu-id="f943e-111">Meta veri öğesi tanımlayan etiket.</span><span class="sxs-lookup"><span data-stu-id="f943e-111">A tag that identifies the metadata item.</span></span> <span data-ttu-id="f943e-112">Atanabilir bazı değerler <xref:System.Drawing.Imaging.PropertyItem.Id%2A> aşağıdaki tabloda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f943e-112">Some values that can be assigned to <xref:System.Drawing.Imaging.PropertyItem.Id%2A> are shown in the following table.</span></span>  
  
|<span data-ttu-id="f943e-113">Onaltılık değeri</span><span class="sxs-lookup"><span data-stu-id="f943e-113">Hexadecimal value</span></span>|<span data-ttu-id="f943e-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f943e-114">Description</span></span>|  
|-----------------------|-----------------|  
|<span data-ttu-id="f943e-115">0x0320</span><span class="sxs-lookup"><span data-stu-id="f943e-115">0x0320</span></span><br /><br /> <span data-ttu-id="f943e-116">0x010F</span><span class="sxs-lookup"><span data-stu-id="f943e-116">0x010F</span></span><br /><br /> <span data-ttu-id="f943e-117">0x0110</span><span class="sxs-lookup"><span data-stu-id="f943e-117">0x0110</span></span><br /><br /> <span data-ttu-id="f943e-118">0x9003</span><span class="sxs-lookup"><span data-stu-id="f943e-118">0x9003</span></span><br /><br /> <span data-ttu-id="f943e-119">0x829A</span><span class="sxs-lookup"><span data-stu-id="f943e-119">0x829A</span></span><br /><br /> <span data-ttu-id="f943e-120">0x5090</span><span class="sxs-lookup"><span data-stu-id="f943e-120">0x5090</span></span><br /><br /> <span data-ttu-id="f943e-121">0x5091</span><span class="sxs-lookup"><span data-stu-id="f943e-121">0x5091</span></span>|<span data-ttu-id="f943e-122">Görüntü başlığı</span><span class="sxs-lookup"><span data-stu-id="f943e-122">Image title</span></span><br /><br /> <span data-ttu-id="f943e-123">Donanım üreticisi</span><span class="sxs-lookup"><span data-stu-id="f943e-123">Equipment manufacturer</span></span><br /><br /> <span data-ttu-id="f943e-124">Donanım modeli</span><span class="sxs-lookup"><span data-stu-id="f943e-124">Equipment model</span></span><br /><br /> <span data-ttu-id="f943e-125">ExifDTOriginal</span><span class="sxs-lookup"><span data-stu-id="f943e-125">ExifDTOriginal</span></span><br /><br /> <span data-ttu-id="f943e-126">EXIF Etkilenme zamanı</span><span class="sxs-lookup"><span data-stu-id="f943e-126">Exif exposure time</span></span><br /><br /> <span data-ttu-id="f943e-127">Aydınlatma tablosu</span><span class="sxs-lookup"><span data-stu-id="f943e-127">Luminance table</span></span><br /><br /> <span data-ttu-id="f943e-128">Chrominance tablosu</span><span class="sxs-lookup"><span data-stu-id="f943e-128">Chrominance table</span></span>|  
  
## <a name="value"></a><span data-ttu-id="f943e-129">Değer</span><span class="sxs-lookup"><span data-stu-id="f943e-129">Value</span></span>  
 <span data-ttu-id="f943e-130">Değerleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="f943e-130">An array of values.</span></span> <span data-ttu-id="f943e-131">Değerlerin biçimi tarafından belirlenen <xref:System.Drawing.Imaging.PropertyItem.Type%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="f943e-131">The format of the values is determined by the <xref:System.Drawing.Imaging.PropertyItem.Type%2A> property.</span></span>  
  
## <a name="len"></a><span data-ttu-id="f943e-132">Len</span><span class="sxs-lookup"><span data-stu-id="f943e-132">Len</span></span>  
 <span data-ttu-id="f943e-133">Tarafından uzunluğu (bayt cinsinden) değerleri dizisi işaret için <xref:System.Drawing.Imaging.PropertyItem.Value%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="f943e-133">The length (in bytes) of the array of values pointed to by the <xref:System.Drawing.Imaging.PropertyItem.Value%2A> property.</span></span>  
  
## <a name="type"></a><span data-ttu-id="f943e-134">Tür</span><span class="sxs-lookup"><span data-stu-id="f943e-134">Type</span></span>  
 <span data-ttu-id="f943e-135">Tarafından dizideki veri türünü işaret için `Value` özelliği.</span><span class="sxs-lookup"><span data-stu-id="f943e-135">The data type of the values in the array pointed to by the `Value` property.</span></span> <span data-ttu-id="f943e-136">Biçimler belirtilen tarafından `Type` özellik değerleri aşağıdaki tabloda gösterilen</span><span class="sxs-lookup"><span data-stu-id="f943e-136">The formats indicated by the `Type` property values are shown in the following table</span></span>  
  
|<span data-ttu-id="f943e-137">Sayısal değer</span><span class="sxs-lookup"><span data-stu-id="f943e-137">Numeric value</span></span>|<span data-ttu-id="f943e-138">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f943e-138">Description</span></span>|  
|-------------------|-----------------|  
|<span data-ttu-id="f943e-139">1.</span><span class="sxs-lookup"><span data-stu-id="f943e-139">1</span></span>|<span data-ttu-id="f943e-140">A`Byte`</span><span class="sxs-lookup"><span data-stu-id="f943e-140">A `Byte`</span></span>|  
|<span data-ttu-id="f943e-141">2</span><span class="sxs-lookup"><span data-stu-id="f943e-141">2</span></span>|<span data-ttu-id="f943e-142">Bir dizi `Byte` ASCII olarak kodlanmış nesneleri</span><span class="sxs-lookup"><span data-stu-id="f943e-142">An array of `Byte` objects encoded as ASCII</span></span>|  
|<span data-ttu-id="f943e-143">3</span><span class="sxs-lookup"><span data-stu-id="f943e-143">3</span></span>|<span data-ttu-id="f943e-144">Bir 16 bit tam sayı</span><span class="sxs-lookup"><span data-stu-id="f943e-144">A 16-bit integer</span></span>|  
|<span data-ttu-id="f943e-145">4</span><span class="sxs-lookup"><span data-stu-id="f943e-145">4</span></span>|<span data-ttu-id="f943e-146">Bir 32 bit tamsayı</span><span class="sxs-lookup"><span data-stu-id="f943e-146">A 32-bit integer</span></span>|  
|<span data-ttu-id="f943e-147">5</span><span class="sxs-lookup"><span data-stu-id="f943e-147">5</span></span>|<span data-ttu-id="f943e-148">İki bir dizi `Byte` rasyonel sayıyı temsil eden nesneler</span><span class="sxs-lookup"><span data-stu-id="f943e-148">An array of two `Byte` objects that represent a rational number</span></span>|  
|<span data-ttu-id="f943e-149">6</span><span class="sxs-lookup"><span data-stu-id="f943e-149">6</span></span>|<span data-ttu-id="f943e-150">Kullanılan değil</span><span class="sxs-lookup"><span data-stu-id="f943e-150">Not used</span></span>|  
|<span data-ttu-id="f943e-151">7</span><span class="sxs-lookup"><span data-stu-id="f943e-151">7</span></span>|<span data-ttu-id="f943e-152">Tanımlanmamış</span><span class="sxs-lookup"><span data-stu-id="f943e-152">Undefined</span></span>|  
|<span data-ttu-id="f943e-153">8</span><span class="sxs-lookup"><span data-stu-id="f943e-153">8</span></span>|<span data-ttu-id="f943e-154">Kullanılan değil</span><span class="sxs-lookup"><span data-stu-id="f943e-154">Not used</span></span>|  
|<span data-ttu-id="f943e-155">9</span><span class="sxs-lookup"><span data-stu-id="f943e-155">9</span></span>|`SLong`|  
|<span data-ttu-id="f943e-156">10</span><span class="sxs-lookup"><span data-stu-id="f943e-156">10</span></span>|`SRational`|  
  
## <a name="example"></a><span data-ttu-id="f943e-157">Örnek</span><span class="sxs-lookup"><span data-stu-id="f943e-157">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="f943e-158">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f943e-158">Description</span></span>  
 <span data-ttu-id="f943e-159">Aşağıdaki kod örneğinde okur ve dosyadaki meta veriler yedi parçalarını görüntüler `FakePhoto.jpg`.</span><span class="sxs-lookup"><span data-stu-id="f943e-159">The following code example reads and displays the seven pieces of metadata in the file `FakePhoto.jpg`.</span></span> <span data-ttu-id="f943e-160">Listede ikinci (dizin 1) özelliği öğesi var. <xref:System.Drawing.Imaging.PropertyItem.Id%2A> 0x010F (donanım üreticisi) ve <xref:System.Drawing.Imaging.PropertyItem.Type%2A> 2 (ASCII kodlu bayt dizesi).</span><span class="sxs-lookup"><span data-stu-id="f943e-160">The second (index 1) property item in the list has <xref:System.Drawing.Imaging.PropertyItem.Id%2A> 0x010F (equipment manufacturer) and <xref:System.Drawing.Imaging.PropertyItem.Type%2A> 2 (ASCII-encoded byte array).</span></span> <span data-ttu-id="f943e-161">Kod örneği, bu özellik öğesinin değeri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="f943e-161">The code example displays the value of that property item.</span></span>  
  
 <span data-ttu-id="f943e-162">Kod aşağıdakine benzer bir çıktı üretir:</span><span class="sxs-lookup"><span data-stu-id="f943e-162">The code produces output similar to the following:</span></span>  
  
 `Property Item 0`  
  
 `id: 0x320`  
  
 `type: 2`  
  
 `length: 16 bytes`  
  
 `Property Item 1`  
  
 `id: 0x10f`  
  
 `type: 2`  
  
 `length: 17 bytes`  
  
 `Property Item 2`  
  
 `id: 0x110`  
  
 `type: 2`  
  
 `length: 7 bytes`  
  
 `Property Item 3`  
  
 `id: 0x9003`  
  
 `type: 2`  
  
 `length: 20 bytes`  
  
 `Property Item 4`  
  
 `id: 0x829a`  
  
 `type: 5`  
  
 `length: 8 bytes`  
  
 `Property Item 5`  
  
 `id: 0x5090`  
  
 `type: 3`  
  
 `length: 128 bytes`  
  
 `Property Item 6`  
  
 `id: 0x5091`  
  
 `type: 3`  
  
 `length: 128 bytes`  
  
 `The equipment make is Northwind Camera.`  
  
### <a name="code"></a><span data-ttu-id="f943e-163">Kod</span><span class="sxs-lookup"><span data-stu-id="f943e-163">Code</span></span>  
 [!code-csharp[System.Drawing.WorkingWithImages#51](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.WorkingWithImages#51](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#51)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f943e-164">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="f943e-164">Compiling the Code</span></span>  
 <span data-ttu-id="f943e-165">Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="f943e-165">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="f943e-166">Formun işlemek <xref:System.Windows.Forms.Control.Paint> olay ve bu kodu boyama olay işleyicisi yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="f943e-166">Handle the form's <xref:System.Windows.Forms.Control.Paint> event and paste this code into the paint event handler.</span></span> <span data-ttu-id="f943e-167">Değiştirmeniz gereken `FakePhoto.jpg` görüntü adı ve yolu, sistem ve içeri aktarma geçerli olan `System.Drawing.Imaging` ad alanı.</span><span class="sxs-lookup"><span data-stu-id="f943e-167">You must replace `FakePhoto.jpg` with an image name and path valid on your system and import the `System.Drawing.Imaging` namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f943e-168">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f943e-168">See Also</span></span>  
 [<span data-ttu-id="f943e-169">Resimler, bit eşlemler ve meta dosyaları</span><span class="sxs-lookup"><span data-stu-id="f943e-169">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [<span data-ttu-id="f943e-170">Resimler, bit eşlemler, simgeler ve meta dosyaları ile çalışma</span><span class="sxs-lookup"><span data-stu-id="f943e-170">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
