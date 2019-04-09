---
title: 'Nasıl yapılır: Görüntü Meta Verilerini Okuma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- metadata [Windows Forms], property item
- metadata [Windows Forms], reading image
ms.assetid: 72ec0b31-0be7-444a-9575-1dbcb864e0be
ms.openlocfilehash: 0a53e9b9d23c03715bf3088a4ae8577a39527995
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59173621"
---
# <a name="how-to-read-image-metadata"></a><span data-ttu-id="2820d-102">Nasıl yapılır: Görüntü Meta Verilerini Okuma</span><span class="sxs-lookup"><span data-stu-id="2820d-102">How to: Read Image Metadata</span></span>
<span data-ttu-id="2820d-103">Bazı görüntü dosyaları, görüntü özelliklerini belirlemek için okuyabilecekleri meta veriler içerir.</span><span class="sxs-lookup"><span data-stu-id="2820d-103">Some image files contain metadata that you can read to determine features of the image.</span></span> <span data-ttu-id="2820d-104">Örneğin, dijital hello'nun marka ve model görüntü yakalamak için kullanılan kameranın belirlemek için okuyabilecekleri bir meta veri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="2820d-104">For example, a digital photograph might contain metadata that you can read to determine the make and model of the camera used to capture the image.</span></span> <span data-ttu-id="2820d-105">İle [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], var olan meta verileri okuyabilir ve görüntü dosyaları ayrıca yeni meta veriler yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2820d-105">With [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], you can read existing metadata, and you can also write new metadata to image files.</span></span>  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="2820d-106">meta verilerde tek bir parçası olarak depolayan bir <xref:System.Drawing.Imaging.PropertyItem> nesne.</span><span class="sxs-lookup"><span data-stu-id="2820d-106">stores an individual piece of metadata in a <xref:System.Drawing.Imaging.PropertyItem> object.</span></span> <span data-ttu-id="2820d-107">Okuyabilirsiniz <xref:System.Drawing.Image.PropertyItems%2A> özelliği bir <xref:System.Drawing.Image> bir dosyanın tüm meta verileri alınacak nesne.</span><span class="sxs-lookup"><span data-stu-id="2820d-107">You can read the <xref:System.Drawing.Image.PropertyItems%2A> property of an <xref:System.Drawing.Image> object to retrieve all the metadata from a file.</span></span> <span data-ttu-id="2820d-108"><xref:System.Drawing.Image.PropertyItems%2A> Özelliği, bir dizi döndürür <xref:System.Drawing.Imaging.PropertyItem> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="2820d-108">The <xref:System.Drawing.Image.PropertyItems%2A> property returns an array of <xref:System.Drawing.Imaging.PropertyItem> objects.</span></span>  
  
 <span data-ttu-id="2820d-109">A <xref:System.Drawing.Imaging.PropertyItem> nesne aşağıdaki dört özelliklere sahiptir: `Id`, `Value`, `Len`, ve `Type`.</span><span class="sxs-lookup"><span data-stu-id="2820d-109">A <xref:System.Drawing.Imaging.PropertyItem> object has the following four properties: `Id`, `Value`, `Len`, and `Type`.</span></span>  
  
## <a name="id"></a><span data-ttu-id="2820d-110">Kimliği</span><span class="sxs-lookup"><span data-stu-id="2820d-110">Id</span></span>  
 <span data-ttu-id="2820d-111">Meta veri öğesini tanımlayan etiket.</span><span class="sxs-lookup"><span data-stu-id="2820d-111">A tag that identifies the metadata item.</span></span> <span data-ttu-id="2820d-112">Atanabilir bazı değerler <xref:System.Drawing.Imaging.PropertyItem.Id%2A> aşağıdaki tabloda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="2820d-112">Some values that can be assigned to <xref:System.Drawing.Imaging.PropertyItem.Id%2A> are shown in the following table.</span></span>  
  
|<span data-ttu-id="2820d-113">Onaltılık değer</span><span class="sxs-lookup"><span data-stu-id="2820d-113">Hexadecimal value</span></span>|<span data-ttu-id="2820d-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2820d-114">Description</span></span>|  
|-----------------------|-----------------|  
|<span data-ttu-id="2820d-115">0x0320</span><span class="sxs-lookup"><span data-stu-id="2820d-115">0x0320</span></span><br /><br /> <span data-ttu-id="2820d-116">0x010F</span><span class="sxs-lookup"><span data-stu-id="2820d-116">0x010F</span></span><br /><br /> <span data-ttu-id="2820d-117">0x0110</span><span class="sxs-lookup"><span data-stu-id="2820d-117">0x0110</span></span><br /><br /> <span data-ttu-id="2820d-118">0x9003</span><span class="sxs-lookup"><span data-stu-id="2820d-118">0x9003</span></span><br /><br /> <span data-ttu-id="2820d-119">0x829A</span><span class="sxs-lookup"><span data-stu-id="2820d-119">0x829A</span></span><br /><br /> <span data-ttu-id="2820d-120">0x5090</span><span class="sxs-lookup"><span data-stu-id="2820d-120">0x5090</span></span><br /><br /> <span data-ttu-id="2820d-121">0x5091</span><span class="sxs-lookup"><span data-stu-id="2820d-121">0x5091</span></span>|<span data-ttu-id="2820d-122">Resmin başlığı</span><span class="sxs-lookup"><span data-stu-id="2820d-122">Image title</span></span><br /><br /> <span data-ttu-id="2820d-123">Donanım üreticisi</span><span class="sxs-lookup"><span data-stu-id="2820d-123">Equipment manufacturer</span></span><br /><br /> <span data-ttu-id="2820d-124">Donanım modeli</span><span class="sxs-lookup"><span data-stu-id="2820d-124">Equipment model</span></span><br /><br /> <span data-ttu-id="2820d-125">ExifDTOriginal</span><span class="sxs-lookup"><span data-stu-id="2820d-125">ExifDTOriginal</span></span><br /><br /> <span data-ttu-id="2820d-126">EXIF tehditlere maruz kalabileceği süreyi</span><span class="sxs-lookup"><span data-stu-id="2820d-126">Exif exposure time</span></span><br /><br /> <span data-ttu-id="2820d-127">Aydınlatma tablo</span><span class="sxs-lookup"><span data-stu-id="2820d-127">Luminance table</span></span><br /><br /> <span data-ttu-id="2820d-128">Chrominance tablo</span><span class="sxs-lookup"><span data-stu-id="2820d-128">Chrominance table</span></span>|  
  
## <a name="value"></a><span data-ttu-id="2820d-129">Değer</span><span class="sxs-lookup"><span data-stu-id="2820d-129">Value</span></span>  
 <span data-ttu-id="2820d-130">Değerleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="2820d-130">An array of values.</span></span> <span data-ttu-id="2820d-131">Değerlerin biçimini tarafından belirlenen <xref:System.Drawing.Imaging.PropertyItem.Type%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="2820d-131">The format of the values is determined by the <xref:System.Drawing.Imaging.PropertyItem.Type%2A> property.</span></span>  
  
## <a name="len"></a><span data-ttu-id="2820d-132">Len</span><span class="sxs-lookup"><span data-stu-id="2820d-132">Len</span></span>  
 <span data-ttu-id="2820d-133">Değerler dizisi uzunluğu (bayt cinsinden) tarafından işaret edilen <xref:System.Drawing.Imaging.PropertyItem.Value%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="2820d-133">The length (in bytes) of the array of values pointed to by the <xref:System.Drawing.Imaging.PropertyItem.Value%2A> property.</span></span>  
  
## <a name="type"></a><span data-ttu-id="2820d-134">Tür</span><span class="sxs-lookup"><span data-stu-id="2820d-134">Type</span></span>  
 <span data-ttu-id="2820d-135">Dizideki değerleri veri türü tarafından işaret edilen `Value` özelliği.</span><span class="sxs-lookup"><span data-stu-id="2820d-135">The data type of the values in the array pointed to by the `Value` property.</span></span> <span data-ttu-id="2820d-136">Tarafından belirtilen biçimleri `Type` özellik değerleri aşağıdaki tabloda gösterilen</span><span class="sxs-lookup"><span data-stu-id="2820d-136">The formats indicated by the `Type` property values are shown in the following table</span></span>  
  
|<span data-ttu-id="2820d-137">Sayısal değer</span><span class="sxs-lookup"><span data-stu-id="2820d-137">Numeric value</span></span>|<span data-ttu-id="2820d-138">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2820d-138">Description</span></span>|  
|-------------------|-----------------|  
|<span data-ttu-id="2820d-139">1.</span><span class="sxs-lookup"><span data-stu-id="2820d-139">1</span></span>|<span data-ttu-id="2820d-140">BİR</span><span class="sxs-lookup"><span data-stu-id="2820d-140">A</span></span> `Byte`|  
|<span data-ttu-id="2820d-141">2</span><span class="sxs-lookup"><span data-stu-id="2820d-141">2</span></span>|<span data-ttu-id="2820d-142">Bir dizi `Byte` ASCII kodlamalı nesneler</span><span class="sxs-lookup"><span data-stu-id="2820d-142">An array of `Byte` objects encoded as ASCII</span></span>|  
|<span data-ttu-id="2820d-143">3</span><span class="sxs-lookup"><span data-stu-id="2820d-143">3</span></span>|<span data-ttu-id="2820d-144">Bir 16 bit tam sayı</span><span class="sxs-lookup"><span data-stu-id="2820d-144">A 16-bit integer</span></span>|  
|<span data-ttu-id="2820d-145">4</span><span class="sxs-lookup"><span data-stu-id="2820d-145">4</span></span>|<span data-ttu-id="2820d-146">Bir 32 bit tamsayı</span><span class="sxs-lookup"><span data-stu-id="2820d-146">A 32-bit integer</span></span>|  
|<span data-ttu-id="2820d-147">5</span><span class="sxs-lookup"><span data-stu-id="2820d-147">5</span></span>|<span data-ttu-id="2820d-148">İki `Byte` rasyonel sayı temsil eden nesneleri</span><span class="sxs-lookup"><span data-stu-id="2820d-148">An array of two `Byte` objects that represent a rational number</span></span>|  
|<span data-ttu-id="2820d-149">6</span><span class="sxs-lookup"><span data-stu-id="2820d-149">6</span></span>|<span data-ttu-id="2820d-150">Kullanılan değil</span><span class="sxs-lookup"><span data-stu-id="2820d-150">Not used</span></span>|  
|<span data-ttu-id="2820d-151">7</span><span class="sxs-lookup"><span data-stu-id="2820d-151">7</span></span>|<span data-ttu-id="2820d-152">Tanımlanmadı</span><span class="sxs-lookup"><span data-stu-id="2820d-152">Undefined</span></span>|  
|<span data-ttu-id="2820d-153">8</span><span class="sxs-lookup"><span data-stu-id="2820d-153">8</span></span>|<span data-ttu-id="2820d-154">Kullanılan değil</span><span class="sxs-lookup"><span data-stu-id="2820d-154">Not used</span></span>|  
|<span data-ttu-id="2820d-155">9</span><span class="sxs-lookup"><span data-stu-id="2820d-155">9</span></span>|`SLong`|  
|<span data-ttu-id="2820d-156">10</span><span class="sxs-lookup"><span data-stu-id="2820d-156">10</span></span>|`SRational`|  
  
## <a name="example"></a><span data-ttu-id="2820d-157">Örnek</span><span class="sxs-lookup"><span data-stu-id="2820d-157">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="2820d-158">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2820d-158">Description</span></span>  
 <span data-ttu-id="2820d-159">Aşağıdaki kod örneği okur ve dosyadaki meta verileri yedi parçalarını görüntüler `FakePhoto.jpg`.</span><span class="sxs-lookup"><span data-stu-id="2820d-159">The following code example reads and displays the seven pieces of metadata in the file `FakePhoto.jpg`.</span></span> <span data-ttu-id="2820d-160">Listedeki ikinci (dizin 1) özelliği öğeye sahip <xref:System.Drawing.Imaging.PropertyItem.Id%2A> 0x010F (ekipman üreticisi) ve <xref:System.Drawing.Imaging.PropertyItem.Type%2A> 2 (ASCII kodlamalı bayt dizisi).</span><span class="sxs-lookup"><span data-stu-id="2820d-160">The second (index 1) property item in the list has <xref:System.Drawing.Imaging.PropertyItem.Id%2A> 0x010F (equipment manufacturer) and <xref:System.Drawing.Imaging.PropertyItem.Type%2A> 2 (ASCII-encoded byte array).</span></span> <span data-ttu-id="2820d-161">Kod örneği, bu özellik öğesinin değeri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="2820d-161">The code example displays the value of that property item.</span></span>  
  
 <span data-ttu-id="2820d-162">Kodu aşağıdakine benzer bir çıktı üretir:</span><span class="sxs-lookup"><span data-stu-id="2820d-162">The code produces output similar to the following:</span></span>  
  
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
  
### <a name="code"></a><span data-ttu-id="2820d-163">Kod</span><span class="sxs-lookup"><span data-stu-id="2820d-163">Code</span></span>  
 [!code-csharp[System.Drawing.WorkingWithImages#51](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.WorkingWithImages#51](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#51)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2820d-164">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="2820d-164">Compiling the Code</span></span>  
 <span data-ttu-id="2820d-165">Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="2820d-165">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="2820d-166">Formun işlemek <xref:System.Windows.Forms.Control.Paint> olay ve bu kodu Boya olay işleyicisine yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="2820d-166">Handle the form's <xref:System.Windows.Forms.Control.Paint> event and paste this code into the paint event handler.</span></span> <span data-ttu-id="2820d-167">Değiştirmeniz gereken `FakePhoto.jpg` bir görüntü adı ve yolu içeri aktarma ve sistem geçerli `System.Drawing.Imaging` ad alanı.</span><span class="sxs-lookup"><span data-stu-id="2820d-167">You must replace `FakePhoto.jpg` with an image name and path valid on your system and import the `System.Drawing.Imaging` namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2820d-168">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2820d-168">See also</span></span>

- [<span data-ttu-id="2820d-169">Resimler, Bit Eşlemler ve Meta Dosyaları</span><span class="sxs-lookup"><span data-stu-id="2820d-169">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="2820d-170">Resimler, Bit Eşlemler, Simgeler ve Meta Dosyaları ile Çalışma</span><span class="sxs-lookup"><span data-stu-id="2820d-170">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](working-with-images-bitmaps-icons-and-metafiles.md)
